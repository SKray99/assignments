# Below is the non-graded code for W7-8>1/5
```java
public class Car {
    private int carYear;
    private int purchasePrice;
    private int currentValue;

    public void setCarYear(int userYear) {
        carYear = userYear;
    }

    public int getCarYear() {
        return carYear;
    }

    public void setPurchasePrice(int userPrice) {
        purchasePrice = userPrice;
    }

    public int getPurchasePrice() {
        return purchasePrice;
    }

    public void calcCurrentValue(int currentYear) {
        double depreciationRate = 0.15;
        int carAge = currentYear - carYear;
        currentValue = (int) Math.round(purchasePrice * Math.pow((1 - depreciationRate), carAge));
    }

    public void printInfo() {
        System.out.println("Car's info:");
        System.out.println("  Model year: " + carYear);
        System.out.println("  Purchase price: $" + purchasePrice);
        System.out.println("  Current value: $" + currentValue);
    }
}
```
```java
import java.util.Scanner;
import java.lang.Math;

public class CarValue {
    public static void main(String[] args) {
        Scanner scnr = new Scanner(System.in);

        Car myCar = new Car();

        int year = scnr.nextInt();
        int price = scnr.nextInt();
        int currentYear = scnr.nextInt();

        myCar.setCarYear(year);
        myCar.setPurchasePrice(price);
        myCar.calcCurrentValue(currentYear);

        myCar.printInfo();
    }
}
```
