// Класс товара
public class Product {
    private int id;
    private String name;
    private String description;
    private double price;
    private int quantityAvailable;
    private int quantityInOrder;
    private int orderId;

    public Product(int id, String name, String description, double price, int quantityAvailable, int quantityInOrder, int orderId) {
        this.id = id;
        this.name = name;
        this.description = description;
        this.price = price;
        this.quantityAvailable = quantityAvailable;
        this.quantityInOrder = quantityInOrder;
        this.orderId = orderId;
    }

    @Override
    public String toString() {
        return "Product{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", description='" + description + '\'' +
                ", price=" + price +
                ", quantityAvailable=" + quantityAvailable +
                ", quantityInOrder=" + quantityInOrder +
                ", orderId=" + orderId +
                '}';
    }
}

// Интерфейс для взаимодействия с клиентом
public interface OnlineShop {
    void showAvailableProducts(); // Показать доступные товары

    String orderProduct(int productId, int quantity); // Заказать товар по id и указанному количеству

    void showOrderedProducts(); // Показать заказанные товары
}

// Реализация интерфейса
public class OnlineShopImpl implements OnlineShop {
    private List<Product> products = new ArrayList<>();

    @Override
    public void showAvailableProducts() {
        for (Product product : products) {
            System.out.println(product.toString());
        }
    }

    @Override
    public String orderProduct(int productId, int quantity) {
        for (Product product : products) {
            if (product.getId() == productId) {
                if (quantity <= product.getQuantityAvailable()) {
                    product.setQuantityInOrder(product.getQuantityInOrder() + quantity);
                    product.setQuantityAvailable(product.getQuantityAvailable() - quantity);
                    product.setOrderId(1); // Устанавливаем айди заказа
                    return product.toString();
                } else {
                    return "Недостаточно товара в наличии";
                }
            }
        }
        return "Товар с указанным id не найден";
    }

    @Override
    public void showOrderedProducts() {
        List<Product> orderedProducts = products.stream()
                .filter(product -> product.getQuantityInOrder() > 0)
                .collect(Collectors.toList());
        for (Product product : orderedProducts) {
            System.out.println(product.toString());
        }
    }
}
