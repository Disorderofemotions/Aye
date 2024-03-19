import java.util.ArrayList;
import java.util.Scanner;

class Plant {
    private int id;
    private String name;
    private String description;
    private long timeHarvest;
    private long timeStart;

    public Plant(int id, String name, String description, long timeHarvest, long timeStart) {
        this.id = id;
        this.name = name;
        this.description = description;
        this.timeHarvest = timeHarvest;
        this.timeStart = timeStart;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getDescription() {
        return description;
    }

    public long getTimeHarvest() {
        return timeHarvest;
    }

    public long getTimeStart() {
        return timeStart;
    }
}

public class GardenerApp {
    private static ArrayList<Plant> plants = new ArrayList<>();
    private static int nextId = 1;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("Menu:");
            System.out.println("1. View all plants");
            System.out.println("2. Add a plant");
            System.out.println("3. Exit");

            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    viewAllPlants();
                    break;
                case 2:
                    addPlant();
                    break;
                case 3:
                    System.out.println("Exiting application...");
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        } while (choice != 3);
    }

    private static void viewAllPlants() {
        System.out.println("All plants:");
        for (Plant plant : plants) {
            System.out.println("ID: " + plant.getId());
            System.out.println("Name: " + plant.getName());
            System.out.println("Description: " + plant.getDescription());
            System.out.println("Time to harvest: " + plant.getTimeHarvest() + " days");
            System.out.println("Time started: " + plant.getTimeStart());
            System.out.println();
        }
    }

    private static void addPlant() {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter plant name: ");
        String name = scanner.nextLine();

        System.out.print("Enter plant description: ");
        String description = scanner.nextLine();

        System.out.print("Enter time to harvest (in days): ");
        long timeHarvest = scanner.nextLong();

        long timeStart = System.currentTimeMillis();

        Plant newPlant = new Plant(nextId, name, description, timeHarvest, timeStart);
        plants.add(newPlant);

        nextId++;

        System.out.println("Plant added successfully.");
    }
}
