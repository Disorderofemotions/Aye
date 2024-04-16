import android.media.MediaPlayer;
import android.os.Bundle;
import android.os.Handler;
import android.widget.Button;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class AlarmActivity extends AppCompatActivity {

    private TextView dayEditText;
    private TextView timeEditText;
    private Button snoozeButton;
    private MediaPlayer mediaPlayer;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_alarm);

        dayEditText = findViewById(R.id.dayEditText);
        timeEditText = findViewById(R.id.timeEditText);
        snoozeButton = findViewById(R.id.snoozeButton);

        int hour = getIntent().getIntExtra("hour", 0);
        int minute = getIntent().getIntExtra("minute", 0);

        timeEditText.setText(String.format("%02d:%02d", hour, minute));

        mediaPlayer = MediaPlayer.create(this, R.raw.alarm_sound);
        mediaPlayer.start();

        snoozeButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                mediaPlayer.stop();
                mediaPlayer.release();
                finish();
            }
        });
    }
}
