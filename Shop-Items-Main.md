//Main
```java
import java.util.Scanner;

public class Main {
  private static Shop shop = new Shop();
  private static Scanner scanner = new Scanner(System.in);
  public static void main(String[] args) {
    
    while(true){
      displayMenu();
      int userInput = scanner.nextInt();
      
      if(userInput == 1){
        addItem();
      }else if(userInput == 2){
        removeItem();
              
      }else if(userInput == 3){
        updateItem();
              
      }else if(userInput == 4){
        addItemToCart();
              
      }else if(userInput == 5){
        checkout();
              
      }else if(userInput == 6){
        System.out.println("Exiting...");
        break;
      }else{
        System.out.println("Invalid option. Please try again.");
      }
    }
    scanner.close();
  }
  public static void displayMenu() {
    System.out.println("Press 1 to add item to the list");
    System.out.println("Press 2 to remove item from the list");
    System.out.println("Press 3 to update the data");
    System.out.println("Press 4 to add items to the cart");
    System.out.println("Press 5 for checkout");
    System.out.println("Press 6 to exit");
    
  }
  public static void addItem() {
      System.out.print("Enter item ID: ");
      int id = scanner.nextInt();
      scanner.nextLine();
      System.out.print("Enter item name: ");
      String name = scanner.nextLine();
      System.out.print("Enter item cost: ");
      int cost = scanner.nextInt();

      Item newItem = new Item(id);
      newItem.setName(name);
      newItem.setCost(cost);
      shop.addItem(newItem);
      System.out.println("Item added successfully.");
  }
  public static void removeItem() {
      System.out.print("Enter item ID to remove: ");
      int removeId = scanner.nextInt();
      shop.removeItem(removeId);
      System.out.println("Item removed successfully.");
  }
  public static void updateItem() {
      System.out.print("Enter item ID to update: ");
      int updateId = scanner.nextInt();
      scanner.nextLine(); 
      System.out.print("Enter new item name: ");
      String newName = scanner.nextLine();
      System.out.print("Enter new item cost: ");
      int newCost = scanner.nextInt();
      shop.updateItem(updateId, newName, newCost);
      System.out.println("Item updated successfully.");
  }
  public static void addItemToCart() {
    System.out.print("Enter item ID to add to cart: ");
    int addCartId = scanner.nextInt();
    Item itemToAdd = null;
    for (Item item : shop.getItems()) {
      if (item.getId() == addCartId) {
        itemToAdd = item;
        break;
      }
    }if (itemToAdd != null) {
      shop.addItemToCart(itemToAdd);
      System.out.println("Item added to cart.");
    }else{
      System.out.println("Item not found.");
    }
  }
  public static void checkout() {
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

  public Item(int id){
    this.id = id;
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
public class Shop{
  private ArrayList<Item> items = new ArrayList<Item>();
  private ArrayList<Item> cart = new ArrayList<Item>();

  public ArrayList<Item> getItems(){
    return items;
  }  
  public void addItem(Item item){
    items.add(item);
  }
  public void removeItem(int id){
    for (var item : items){
      if (item.getId() == id){
        items.remove(item);
        return;
      }
    }
  }
  public void updateItem(int id, String name, int cost){
    for (var item : items){
      if(item.getId() == id){
        item.setName(name);
        item.setCost(cost);
        return;
      }
    }
  }
    public void addItemToCart(Item item){
      cart.add(item);
    }
  public int checkout(){ 
    int sum = 0;
    for(var item : cart){
      sum += item.getCost();
    }
    return sum;
  }
}
```





