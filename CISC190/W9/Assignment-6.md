# This is my W9>1/1 code:
```java
import java.util.Scanner;

public class Pedometer {

    public static double stepsToMiles(int steps) throws Exception {
        if (steps < 0) {
            throw new Exception("Exception: Negative step count entered.");
        }
        return steps / 2000.0;
    }

    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);

        System.out.print("Enter number of steps: ");
        int steps = scnr.nextInt();

        try {
            double miles = stepsToMiles(steps);
            System.out.printf("%.2f\n", miles);
        } catch (Exception e) {
            System.out.println(e.getMessage());
        }

        scnr.close();
    }
}
```
## Note: To make testing easier, I added a prompt asking users to input steps.
#
#
#
#
#
# NO MORE ENTRIES FOR THIS ASSIGNMENT
