
PulseGPT - AI Assistant:
Конечно, я могу помочь с написанием кода для приложения ежедневника с двумя экранами, кнопкой "Добавить" и использованием SQLiteHelper. Вот пример кода на языке Java:

1. Создайте класс DatabaseHelper, который будет расширять SQLiteOpenHelper:

import android.content.Context;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

public class DatabaseHelper extends SQLiteOpenHelper {
    private static final int DATABASE_VERSION = 1;
    private static final String DATABASE_NAME = "TodoListDB";
    private static final String TABLE_NAME = "TodoListTable";
    private static final String COLUMN_ID = "id";
    private static final String COLUMN_TITLE = "title";
    private static final String COLUMN_DATE = "date";
    private static final String COLUMN_TIME = "time";
    private static final String COLUMN_DESCRIPTION = "description";

    public DatabaseHelper(Context context) {
        super(context, DATABASE_NAME, null, DATABASE_VERSION);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        String query = "CREATE TABLE " + TABLE_NAME + " (" +
                COLUMN_ID + " INTEGER PRIMARY KEY AUTOINCREMENT, " +
                COLUMN_TITLE + " TEXT, " +
                COLUMN_DATE + " TEXT, " +
                COLUMN_TIME + " TEXT, " +
                COLUMN_DESCRIPTION + " TEXT)";
        db.execSQL(query);
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        db.execSQL("DROP TABLE IF EXISTS " + TABLE_NAME);
        onCreate(db);
    }
}
2. Создайте класс MainActivity, который будет отображать первый экран с названием дел, датой, временем и описанием:

`java
import android.content.Intent;
import android.database.sqlite.SQLiteDatabase;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private EditText titleEditText, dateEditText, timeEditText, descriptionEditText;
    private Button addButton;
    private DatabaseHelper databaseHelper;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        titleEditText = findViewById(R.id.titleEditText);
        dateEditText = findViewById(R.id.dateEditText);
        timeEditText = findViewById(R.id.timeEditText);
        descriptionEditText = findViewById(R.id.descriptionEditText);
        addButton = findViewById(R.id.addButton);

        databaseHelper = new DatabaseHelper(this);
        final SQLiteDatabase database = databaseHelper.getWritableDatabase();

        addButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String title = titleEditText.getText().toString();
                String date = dateEditText.getText().toString();
                String time = timeEditText.getText().toString();
                String description = descriptionEditText.getText().toString();

                // Вставка записи в базу данных
                String query = "INSERT INTO " + DatabaseHelper.TABLE_NAME + " (" +
                        DatabaseHelper.COLUMN_TITLE + ", " +
                        DatabaseHelper.COLUMN_DATE + ", " +
                        DatabaseHelper.COLUMN_TIME + ", " +
                        DatabaseHelper.COLUMN_DESCRIPTION + ") VALUES ('" +
                        title + "', '" + date + "', '" + time + "', '" + description + "')";
                database.execSQL(query);

                // Очистка полей ввода
                titleEditText.setText("");
                dateEditText.setText("");
                timeEditText.setText("");
                descriptionEditText.setText("");

                // Переход на второй экран
