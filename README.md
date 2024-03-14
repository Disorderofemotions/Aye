import java.util.*;
import java.util.stream.Collectors;

class Food {
    private int id;
    private String name;
    private String description;

    public Food(int id, String name, String description) {
        this.id = id;
        this.name = name;
        this.description = description;
    }

    @Override
    public String toString() {
        return "Food{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", description='" + description + '\'' +
                '}';
    }
}

public class Main {
    private static List<Food> arrayList = new ArrayList<>();
    private static Set<Food> hashSet = new HashSet<>();
    private static LinkedList<Food> linkedList = new LinkedList<>();
    private static Set<Food> set = new TreeSet<>();
    private static Vector<Food> vector = new Vector<>();

    public static void main(String[] args) {
        Random random = new Random();
        for (int i = 0; i < 100000; i++) {
            Food food = new Food(i, "Food " + i, "Description " + i);
            arrayList.add(food);
            hashSet.add(food);
            linkedList.add(food);
            set.add(food);
            vector.add(food);
        }

        System.out.println("Выберите массив (1 - ArrayList, 2 - HashSet, 3 - LinkedList, 4 - TreeSet, 5 - Vector): ");
        Scanner scanner = new Scanner(System.in);
        int choice = scanner.nextInt();

        switch (choice) {
            case 1:
                manipulateList(arrayList);
                break;
            case 2:
                manipulateSet(hashSet);
                break;
            case 3:
                manipulateList(linkedList);
                break;
            case 4:
                manipulateSet(set);
                break;
            case 5:
                manipulateList(vector);
                break;
            default:
                System.out.println("Некорректный выбор массива.");
                break;
        }
    }

    private static void manipulateList(List<Food> list) {
        System.out.println("Выберите действие (1 - Добавить элемент, 2 - Удалить элемент, 3 - Модификация элемента):");
        Scanner scanner = new Scanner(System.in);
        int action = scanner.nextInt();

        switch (action) {
            case 1:
                System.out.println("Выберите место для добавления (1 - в начало, 2 - в середину, 3 - в конец):");
                int addChoice = scanner.nextInt();
                System.out.println("Введите данные для нового элемента (Id, Name, Description):");
                Food newFood = new Food(scanner.nextInt(), scanner.next(), scanner.next());
                switch (addChoice) {
                    case 1:
                        list.add(0, newFood);
                        break;
                    case 2:
                        int mid = list.size() / 2;
                        list.add(mid, newFood);
                        break;
                    case 3:
                        list.add(newFood);
                        break;
                    default:
                        System.out.println("Некорректный выбор места для добавления.");
                        break;
                }
                break;
            case 2:
                System.out.println("Введите индекс элемента для удаления:");
                int removeIndex = scanner.nextInt();
                list.remove(removeIndex);
                break;
            case 3:
                System.out.println("Введите индекс элемента для модификации:");
                int modifyIndex = scanner.nextInt();
                System.out.println("Введите новые данные для элемента (Name, Description):");
                list.get(modifyIndex).name = scanner.next();
                list.get(modifyIndex).description = scanner.next();
                break;
            default:
                System.out.println("Некорректное действие.");
                break;
        }

        // Выводим первые 10 элементов списка
        list.stream().limit(10).collect(Collectors.toList()).forEach(System.out::println);
    }

    private static void manipulateSet(Set<Food> set) {
        System.out.println("Выберите действие (1 - Добавить элемент, 2 - Удалить элемент, 3 - Модификация элемента):");
        Scanner scanner = new Scanner(System.in);
        int action = scanner.nextInt();

        switch (action) {
            case 1:
                System.out.println("Введите данные для нового элемента (Id, Name, Description):");
                Food newFood = new Food(scanner.nextInt(), scanner.next(), scanner.next());
                set.add(newFood);
                break;
            case 2:
                System.out.println("Введите Id элемента для удаления:");
                int removeId = scanner.nextInt();
                set.removeIf(food -> food.id == removeId);
                break;
           
