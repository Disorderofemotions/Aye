```java
import java.util.ArrayList;
import java.util.HashSet;
import java.util.LinkedList;
import java.util.Set;
import java.util.Vector;

class Food {
    private int id;
    private String name;
    private String description;

    public Food(int id, String name, String description) {
        this.id = id;
        this.name = name;
        this.description = description;
    }
}

public class Main {
    public static void main(String[] args) {
        ArrayList<Food> arrayList = new ArrayList<>();
        Set<Food> set = new HashSet<>();
        LinkedList<Food> linkedList = new LinkedList<>();
        HashSet<Food> hashSet = new HashSet<>();
        Vector<Food> vector = new Vector<>();

        // Заполнение списка продуктов
        for (int i = 0; i < 100000; i++) {
            Food food = new Food(i, "Food" + i, "Description" + i);
            arrayList.add(food);
            set.add(food);
            linkedList.add(food);
            hashSet.add(food);
            vector.add(food);
        }

        // Добавление одного элемента в начало, в середину и в конец
        Food newFood = new Food(100001, "New Food", "New Description");

        arrayList.add(0, newFood);  // Добавление в начало списка
        linkedList.add(linkedList.size() / 2, newFood); // Добавление в середину списка
        vector.add(newFood); // Добавление в конец списка

        // Удаление одного элемента
        arrayList.remove(0);
        set.remove(newFood);
        linkedList.remove(newFood);
        hashSet.remove(newFood);
        vector.remove(newFood);

        // Модификация одного элемента
        Food foodToModify = arrayList.get(0);
        foodToModify.setName("Modified Food");
        foodToModify.setDescription("Modified Description");

    }
}
```
