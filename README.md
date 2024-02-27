public class BuildingStore {
private int id;
private String name;
private String description;
private double price;
private int number;
private int numberCard;
private int IDcard;public BuildingStore(int id, String name, String description, double price, int number, int numberCard, int IDcard) {
    this.id = id;
    this.name = name;
    this.description = description;
    this.price = price;
    this.number = number;
    this.numberCard = numberCard;
    this.IDcard = IDcard;
}

@Override
public String toString() {
    return "{" +
            "\"id\": " + id + ", " +
            "\"name\": \"" + name + "\", " +
            "\"description\": \"" + description + "\", " +
            "\"price\": " + price + ", " +
            "\"number\": " + number + ", " +
            "\"numberCard\": " + numberCard + ", " +
            "\"IDcard\": " + IDcard +
            "}";
}

public static void main(String[] args) {
    BuildingStore building1 = new BuildingStore(1, "Hammer", "Tool for hitting nails", 10.99, 100, 123456, 987654321);
    System.out.println(building1.toString());
}
