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
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        while (true) {
            System.out.println("Menu:");
            System.out.println("1. View all plants");
            System.out.println("2. Add a plant");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine();

            switch (choice) {
                case 1:
                    viewAllPlants();
                    break;
                case 2:
                    addPlant();
                    break;
                case 3:
                    System.out.println("Exiting the program");
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }

    private static void viewAllPlants() {
        for (Plant plant : plants) {
            System.out.println("Id: " + plant.getId());
            System.out.println("Name: " + plant.getName());
            System.out.println("Description: " + plant.getDescription());
            System.out.println("Time Harvest: " + plant.getTimeHarvest() + " seconds");
            long elapsedTime = (System.currentTimeMillis() - plant.getTimeStart) / 1000;
            if (elapsedTime >= plant.getTimeHarvest) {
                System.out.println(plant.getName() + " has grown!");
            } else {
                System.out.println(plant.getName() + " is still growing.");
            }
            System.out.println();
        }
    }

    private static void addPlant() {
        System.out.print("Enter plant Id: ");
        int id = scanner.nextInt();
        scanner.nextLine();
        System.out.print("Enter plant name: ");
        String name = scanner.nextLine();
        System.out.print("Enter plant description: ");
        String description = scanner.nextLine();
        System.out.print("Enter time to harvest (in seconds): ");
        long timeHarvest = scanner.nextLong();
        Plant newPlant = new Plant(id, name, description, timeHarvest, System.currentTimeMillis());
        plants.add(newPlant);
        System.out.println("Plant added successfully!");
    }
}
