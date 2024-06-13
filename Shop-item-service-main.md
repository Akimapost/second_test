//Main
```java
import java.util.Scanner;
public class Main {
    private static Scanner scanner = new Scanner(System.in);
    private static ItemService itemService = new ItemService();
    private static Shop shop = new Shop();
    public static void main(String[] args) {
        while(true){
          System.out.println("Press 1, to add an item");
          System.out.println("Press 2, to print all items");
          System.out.println("Press 3, to remove item");
          System.out.println("Press 4, to update items");
          System.out.println("Press 5, to add items to the cart");
          System.out.println("Press 6, for checkout");
          System.out.println("Press 7 to exit");
          
            int action = scanner.nextInt();
            if (action == 1){
              addItem();
            } else if (action == 2){
              printItems();
            } else if(action == 3) {
              removeItem();
            } else if (action == 4){
              updateItem();
            } else if (action == 5){
              addItemToCart();
            } else if (action == 6){
              checkout();
            }  else if (action == 7){
              System.out.println("Exiting...");
                break;
                }else{
                  System.out.println("Invalid option. Please try again.");
                }
              }
              scanner.close();
    }

    public static void addItem(){
        System.out.println("Provide an item id"); 
        int id = scanner.nextInt();
        System.out.println("Provide an item name");
        String name = scanner.next();
        System.out.println("Provide an item cost");
        int cost = scanner.nextInt();
        var item = new Item(id, name, cost);
        itemService.addItem(item);
    }

    public static void printItems(){
        System.out.println("These are the items in the storage: ");
        var items = itemService.getItems();
        for (var item : items){
            System.out.println(item.getId() + " " + item.getName()  + " " + item.getCost());
        }
    }
    public static void removeItem(){
        System.out.print("Enter item ID to remove: ");
        int removeId = scanner.nextInt();
        itemService.removeItem(removeId);
        System.out.println("Item removed successfully.");
    }
    public static void updateItem(){
        System.out.print("Enter item ID to update: ");
        int updateId = scanner.nextInt();
        scanner.nextLine(); 
        System.out.print("Enter new item name: ");
        String newName = scanner.nextLine();
        System.out.print("Enter new item cost: ");
        int newCost = scanner.nextInt();
        itemService.updateItem(updateId, newName, newCost);
        System.out.println("Item updated successfully.");
  }
  public static void addItemToCart(){
    System.out.print("Enter item ID to add to cart: ");
    int addCartId = scanner.nextInt();
    Item itemToAdd = null;
    for (Item item : itemService.getItems()){
      if (item.getId() == addCartId){
        itemToAdd = item;
        break;
      }
    }if (itemToAdd != null){
      shop.addItemToCart(itemToAdd);
      System.out.println("Item added to cart.");
    }else{
      System.out.println("Item not found.");
    }
  }
  public static void checkout(){
    int totalCost = shop.checkout();
    System.out.println("Total cost: " + totalCost);
  }
}
```
//Item
```java
public class Item{ 
  private int id;
  private String name; 
  private int cost; 

  public Item(int id, String name, int cost){
    this.id = id;
    this.name = name;
    this.cost = cost;
  }

  public int getId(){
    return id;
  }

  public void setName(String name){
    this.name = name;
  }

  public String getName(){
    return name;
  }

  public void setCost(int cost){
    this.cost = cost;
  }

  public int getCost(){
    return cost;
  }
}
```
//Shop
```java
import java.util.ArrayList;

public class Shop {
  public ArrayList<Item> cart = new ArrayList<Item>();

  public void addItemToCart(Item item) {
    cart.add(item);
  }

  public int checkout() { 
    int sum = 0;
    for (var item : cart) {
      sum += item.getCost();
    }
    return sum;
  }

}
```
//ItemService
```java
import java.util.ArrayList;

public class ItemService{
  
  private ArrayList<Item> items = new ArrayList<Item>();
  
  public ArrayList<Item> getItems() {
    return items;
  }

  public void addItem(Item item) {
    items.add(item);
  }

  public void removeItem(int id) {
    for (var item : items) {
      if (item.getId() == id) {
        items.remove(item);
        return;
      }
    }
  }

  public void updateItem(int id, String name, int cost) {
    for (var item : items) {
      if (item.getId() == id) {
        item.setName(name);
        item.setCost(cost);
        return;
      }
    }
  }
  
}
```





