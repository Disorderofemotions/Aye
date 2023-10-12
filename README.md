# Aye
Конечно, вот пример кода на языке Java для Android Studio:

```java
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private EditText fuelInput;
    private TextView distanceOutput;
    private Button calculateButton;

    private static final int MAX_FUEL_CAPACITY = 50;
    private static final double FUEL_CONSUMPTION = 12.0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        fuelInput = findViewById(R.id.fuel_input);
        distanceOutput = findViewById(R.id.distance_output);
        calculateButton = findViewById(R.id.calculate_button);

        calculateButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                calculateDistance();
            }
        });
    }

    private void calculateDistance() {
        String fuelStr = fuelInput.getText().toString();

        if (fuelStr.isEmpty()) {
            Toast.makeText(this, "Введите количество литров", Toast.LENGTH_SHORT).show();
            return;
        }

        double fuelAmount = Double.parseDouble(fuelStr);

        if (fuelAmount > MAX_FUEL_CAPACITY) {
            Toast.makeText(this, "Ошибка: превышено максимальное количество литров", Toast.LENGTH_SHORT).show();
            return;
        }

        double distance = (fuelAmount / FUEL_CONSUMPTION) * 100.0;
        distanceOutput.setText(String.valueOf(distance) + " км");
    }
}
```

В этом примере мы используем EditText для ввода количества литров топлива, TextView для отображения расстояния и Button для запуска расчета. Мы также добавили проверки на пустой ввод и превышение максимального количества литров. Рассчет расстояния выполняется по формуле `(количество литров / расход топлива) * 100`.
