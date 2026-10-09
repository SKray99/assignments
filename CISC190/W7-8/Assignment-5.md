# Below is the non-graded code for W7-8>1/5
```java
public class Car {
    private int modelYear;
    private int purchasePrice;
    private int currentValue;
    public void setModelYear(int userYear){
        modelYear = userYear;
    }
    
    public int getModelYear() {
        return modelYear;
    }
    
    public void setPurchasePrice(int userPrice) {
        purchasePrice = userPrice;
    }
    
    public int getPurchasePrice() {
        return purchasePrice;
    }
    
    public void calcCurrentValue(int currentYear) {
        double rate = 0.15;
        int age = currentYear - modelYear;
        double formula = purchasePrice * Math.pow((1 - rate), age);
        currentValue = (int) Math.round(formula);
    }
    
    public void printInfo() {
        System.out.println("Car's information:");
        System.out.println("  Model year: " + modelYear);
        System.out.println("  Purchase price: $" + purchasePrice);
        System.out.println("  Current value: $" + currentValue);
    }
}

```
# Below is the non-graded code for W7-8>2/5
```java
public class FoodItem {
    private String name;
    private double fat;
    private double carbs;
    private double protein;
    public FoodItem() {
        name = "Water";
        fat = 0.0;
        carbs = 0.0;
        protein = 0.0;
    }

    public FoodItem(String userName, double userFatAmt, double userCarbAmt, double userProteinAmt) {
        name = userName;
        fat = userFatAmt;
        carbs = userCarbAmt;
        protein = userProteinAmt;
    }

    public String getName() {
        return name;
    }

    public double getFat() {
        return fat;
    }

    public double getCarbs() {
        return carbs;
    }

    public double getProtein() {
        return protein;
    }

    public double getCalories(double numServings) {
        double calories = ((fat * 9) + (carbs * 4) + (protein * 4)) * numServings;
        return calories;
    }

    public void printInfo() {
        System.out.printf("Nutritional information per serving of %s:\n", name);
        System.out.printf("  Fat: %.2f g\n", fat);
        System.out.printf("  Carbohydrates: %.2f g\n", carbs);
        System.out.printf("  Protein: %.2f g\n", protein);
    }
}
```
