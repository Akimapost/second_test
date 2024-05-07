```java
import java.util.Random;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);
        Random generator = new Random();

        int wins = 0;
        int losses = 0;

        while (wins < 3 && losses < 3) {
            String personChoice;
            String compChoice = "";

            int computerInt = generator.nextInt(3) + 1;
            if (computerInt == 1)
                compChoice = "r";
            else if (computerInt == 2)
                compChoice = "p";
            else if (computerInt == 3)
                compChoice = "s";

            System.out.println("Please, choose (r)ock, (p)aper, or (s)cissors:");
            personChoice = scan.next().toLowerCase();

            System.out.println("Computer plays " + compChoice);
            if (personChoice.equals(compChoice)) {
                System.out.println("It's a tie!");
            } else if (personChoice.equals("r")) {
                if (compChoice.equals("s"))
                    System.out.println("Rock crushes scissors. You win!");
                else if (compChoice.equals("p")) {
                    System.out.println("Paper covers rock. You lose!");
                    losses++;
                }
                wins++;
            } else if (personChoice.equals("p")) {
                if (compChoice.equals("s")) {
                    System.out.println("Scissors cuts paper. You lose!");
                    losses++;
                }
                else if (compChoice.equals("r")) {
                    System.out.println("Paper covers rock. You win!");
                    wins++;
                }
            } else if (personChoice.equals("s")) {
                if (compChoice.equals("p")) {
                    System.out.println("Scissors cuts paper. You win!");
                    wins++;
                }
                else if (compChoice.equals("r")) {
                    System.out.println("Rock crushes scissors. You lose!");
                    losses++;
                }
            } else {
                System.out.println("Invalid user input.");
            }
        }
        if (wins >= 3) {
            System.out.println("Congratulations! You win the game!");
        } else {
            System.out.println("Sorry! You lose the game!");
        }
        scan.close();
    }
}
```


