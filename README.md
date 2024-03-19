import java.util.ArrayList;
import java.util.Scanner;

class Plant {
    private int id;
    private String name;
    private String description;
    private long timeToHarvest;
    private long timeStart;

    public Plant(int id, String name, String description, long timeToHarvest) {
        this.id = id;
        this.name = name;
        this.description = description;
        this.timeToHarvest = timeToHarvest;
        this.timeStart = System.currentTimeMillis();
    }

    public void grow() {
        long currentTime = System.currentTimeMillis();
        if (currentTime - timeStart >= timeToHarvest * 1000) {
            System.out.println(name + " has grown!");
        }
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
}

public class GardenerApp {
    private static ArrayList<Plant> plants = new ArrayList<>();
    private static int plantId = 1;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        while (true) {
            System.out.println("Menu:");
            System.out.println("1. View all plants");
            System.out.println("2. Add a plant");
            System.out.println("3. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();
            
            switch (choice) {
                case 1:
                    viewAllPlants();
                    break;
                case 2:
                    addPlant();
                    break;
                case 3:
                    System.out.println("Exiting...");
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }

    private static void viewAllPlants() {
        System.out.println("All Plants:");
        for (Plant plant : plants) {
            plant.grow();
            System.out.println(plant.getId() + ". " + plant.getName() + " - " + plant.getDescription());
        }
    }

    private static void addPlant() {
        Scanner scanner = new Scanner(System.in);
        
        System.out.print("Enter plant name: ");
        String name = scanner.next();
        
        System.out.print("Enter plant description: ");
        String description = scanner.next();
        
        System.out.print("Enter time to harvest (in seconds): ");
        long timeToHarvest = scanner.nextLong();
        
        Plant newPlant = new Plant(plantId, name, description, timeToHarvest);
        plants.add(newPlant);
        plantId++;
        
        System.out.println("Plant added successfully.");
    }
}
