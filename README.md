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

    // getters and setters

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getDescription() {
        return description;
    }

    public void setDescription(String description) {
        this.description = description;
    }
}

public class Main {

    public static void main(String[] args) {
        ArrayList<Food> arrayList = new ArrayList<>();
        LinkedList<Food> linkedList = new LinkedList<>();
        HashSet<Food> hashSet = new HashSet<>();
        Vector<Food> vector = new Vector<>();
        Set<Food> set = new HashSet<>();

        for (int i = 0; i < 100000; i++) {
            Food food = new Food(i, "Food" + i, "Description" + i);
            arrayList.add(food);
            linkedList.add(food);
            hashSet.add(food);
            vector.add(food);
            set.add(food);
        }

        // Add element to the beginning of the list
        Food newFood1 = new Food(100001, "New Food 1", "New Description 1");
        arrayList.add(0, newFood1);
        linkedList.addFirst(newFood1);
        vector.add(0, newFood1);
        set.add(newFood1);

        // Add element to the middle of the list
        Food newFood2 = new Food(100002, "New Food 2", "New Description 2");
        int mid = arrayList.size() / 2;
        arrayList.add(mid, newFood2);
        linkedList.add(mid, newFood2);
        vector.add(mid, newFood2);
        set.add(newFood2);

        // Add element to the end of the list
        Food newFood3 = new Food(100003, "New Food 3", "New Description 3");
        arrayList.add(newFood3);
        linkedList.addLast(newFood3);
        vector.add(newFood3);
        set.add(newFood3);

        // Remove an element
        arrayList.remove(newFood1);
        linkedList.remove(newFood2);
        vector.remove(newFood3);
        set.remove(newFood1);

        // Modify an element
        Food foodToModify = arrayList.get(0);
        foodToModify.setName("Modified Name");
        foodToModify.setDescription("Modified Description");
    }
}
```
