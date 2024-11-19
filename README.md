package garmentmanagement;

import java.util.List;
import java.util.Scanner;
import java.util.ArrayList;
import java.util.Date;

public class GarmentManagement {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter Fabric Code: ");
        String fabricCode = scanner.nextLine();
        System.out.print("Enter Fabric Category: ");
        String fabricCategory = scanner.nextLine();
        System.out.print("Enter Fabric Shade: ");
        String fabricShade = scanner.nextLine();
        System.out.print("Enter Cost Per Meter of Fabric: ");
        double fabricCostPerMeter = scanner.nextDouble();
        System.out.println("================================");
        scanner.nextLine();

        Material fabricMaterial = new Material(fabricCode, fabricCategory, fabricShade, fabricCostPerMeter);

        System.out.print("Enter Garment Code: ");
        String garmentCode = scanner.nextLine();
        System.out.print("Enter Garment Title: ");
        String garmentTitle = scanner.nextLine();
        System.out.print("Enter Garment Details: ");
        String garmentDetails = scanner.nextLine();
        System.out.print("Enter Garment Size: ");
        String garmentSize = scanner.nextLine();
        System.out.print("Enter Garment Color: ");
        String garmentColor = scanner.nextLine();
        System.out.print("Enter Garment Price: ");
        double garmentPrice = scanner.nextDouble();
        System.out.print("Enter Available Stock: ");
        int garmentStock = scanner.nextInt();
        System.out.println("================================");
        scanner.nextLine();

        Apparel garment = new Apparel(garmentCode, garmentTitle, garmentDetails, garmentSize, garmentColor, garmentPrice, garmentStock, fabricMaterial);

        System.out.print("Enter Buyer ID: ");
        String buyerId = scanner.nextLine();
        System.out.print("Enter Buyer Name: ");
        String buyerName = scanner.nextLine();
        System.out.print("Enter Buyer Email: ");
        String buyerEmail = scanner.nextLine();
        System.out.print("Enter Buyer Phone Number: ");
        String buyerPhoneNumber = scanner.nextLine();
        System.out.println("================================");

        Buyer customer = new Buyer(buyerId, buyerName, buyerEmail, buyerPhoneNumber);

        System.out.print("Enter Transaction ID: ");
        String transactionId = scanner.nextLine();
        Date transactionDate = new Date();

        Purchase purchase = new Purchase(transactionId, transactionDate);
        purchase.addItem(garment);
        customer.completePurchase(purchase);
        purchase.displayPurchaseSummary();

        scanner.close();
    }
}

class Apparel {
    public String code;
    public String title;
    public String details;
    public String size;
    public String color;
    public double price;
    public int stock;
    public Material material;

    public Apparel(String code, String title, String details, String size, String color, double price, int stock, Material material) {
        this.code = code;
        this.title = title;
        this.details = details;
        this.size = size;
        this.color = color;
        this.price = price;
        this.stock = stock;
        this.material = material;
    }

    void modifyStock(int newStock) {
        this.stock = newStock;
    }

    double computeDiscountedPrice(double discountRate) {
        return price - (price * discountRate / 100);
    }
}

class Material {
    public String code;
    public String category;
    public String shade;
    public double costPerUnit;

    public Material(String code, String category, String shade, double costPerUnit) {
        this.code = code;
        this.category = category;
        this.shade = shade;
        this.costPerUnit = costPerUnit;
    }
}
