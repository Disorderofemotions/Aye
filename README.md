import android.media.MediaPlayer;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class AlarmActivity extends AppCompatActivity {

    private EditText dayEditText;
    private EditText timeEditText;
    private Button dismissButton;
    private MediaPlayer mediaPlayer;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_alarm);

        mediaPlayer = MediaPlayer.create(this, R.raw.alarm_sound);

        dayEditText = findViewById(R.id.day_edit_text);
        timeEditText = findViewById(R.id.time_edit_text);
        dismissButton = findViewById(R.id.dismiss_button);

        dismissButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                mediaPlayer.stop();
                finish();
            }
        });

        mediaPlayer.start();
    }
}
