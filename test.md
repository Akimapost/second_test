```java
public class Main {
 public static void main(String[] args) {
    int[][] array = new int[10][10];

    for (int i = 0; i < array.length; i++) {
        for (int j = 0; j < array[i].length; j++) {
             if (i % 2 == 1 || j % 2 == 1) {
                array[i][j] = 1;
             }
              if (array[i][j] == 0) {
             System.out.print(" ");
             } else {
             System.out.print(array[i][j]);
             }
        }
        System.out.println();
     }
 }
}
```

