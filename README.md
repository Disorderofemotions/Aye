import com.fasterxml.jackson.core.JsonProcessingException;
import com.fasterxml.jackson.databind.ObjectMapper;

public class StoreMaterial {
    private int id;
    private String name;
    private String description;
    private double price;
    private int number;
    private int numberCard;
    private int idCard;

    public StoreMaterial(int id, String name, String description, double price, int number, int numberCard, int idCard) {
        this.id = id;
        this.name = name;
        this.description = description;
        this.price = price;
        this.number = number;
        this.numberCard = numberCard;
        this.idCard = idCard;
    }

    @Override
    public String toString() {
        ObjectMapper objectMapper = new ObjectMapper();
        try {
            return objectMapper.writeValueAsString(this);
        } catch (JsonProcessingException e) {
            e.printStackTrace();
            return "";
        }
    }

    public static void main(String[] args) {
        StoreMaterial material = new StoreMaterial(1, "Wood", "High quality wood material", 50.0, 100, 1234, 5678);
        System.out.println(material.toString());
    }
}
