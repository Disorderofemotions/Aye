import java.util.*;

class Plane {
    private int id;
    private String name;
    private int year;

    public Plane(int id, String name, int year) {
        this.id = id;
        this.name = name;
        this.year = year;
    }

    public String getName() {
        return name;
    }

    public int getYear() {
        return year;
    }

    @Override
    public String toString() {
        return "Plane{" +
                "name='" + name + '\'' +
                ", year=" + year +
                '}';
    }
}

public class Main {
    public static void main(String[] args) {
        HashSet<Plane> planes = new HashSet<>();

        for (int i = 1; i <= 100; i++) {
            Plane plane = new Plane(i, "Plane" + i, 2000 + i);
            planes.add(plane);
        }

        Scanner scanner = new Scanner(System.in);

        System.out.println("1) Сортировка по имени");
        System.out.println("2) Сортировка по году производства");
        System.out.println("3) Фильтр по имени");
        System.out.println("4) Фильтр по году");
        System.out.println("5) Фильтр по указанному году");

        int choice = scanner.nextInt();
        switch (choice) {
            case 1:
                List<Plane> sortedByName = new ArrayList<>(planes);
                Collections.sort(sortedByName, Comparator.comparing(Plane::getName));
                System.out.println(sortedByName);
                break;
            case 2:
                List<Plane> sortedByYear = new ArrayList<>(planes);
                Collections.sort(sortedByYear, Comparator.comparing(Plane::getYear));
                System.out.println(sortedByYear);
                break;
            case 3:
                System.out.println("Введите символ для фильтрации по имени:");
                String filterName = scanner.next();
                planes.stream()
                        .filter(plane -> plane.getName().contains(filterName))
                        .forEach(System.out::println);
                break;
            case 4:
                System.out.println("Введите год для фильтрации:");
                int filterYear = scanner.nextInt();
                planes.stream()
                        .filter(plane -> plane.getYear() == filterYear)
                        .forEach(System.out::println);
                break;
            case 5:
                System.out.println("Введите год для фильтрации:");
                int inputYear = scanner.nextInt();
                planes.stream()
                        .filter(plane -> plane.getYear() == inputYear)
                        .forEach(System.out::println);
                break;
        }
    }
}
