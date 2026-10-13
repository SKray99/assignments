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
# Below is my code for W7-8>3/5
```java
// ===== Code from file Person.java =====
public class Person {
    private int ageYears;
    private String lastName;

    public void setName(String userName) {
        lastName = userName;
    }

    public void setAge(int numYears) {
        ageYears = numYears;
    }

    // Other parts omitted

    public void printAll() {
        System.out.print("Name: " + lastName);
        System.out.print(", Age: " + ageYears);
    }
}
// ===== end =====

// ===== Code from file Student.java =====
public class Student extends Person {
    private int idNum;

    public void setID(int studentId) {
        idNum = studentId;
    }

    public int getID() {
        return idNum;
    }
}
// ===== end =====

// ===== Code from file StudentDerivationFromPerson.java =====
public class StudentDerivationFromPerson {
    public static void main(String[] args) {
        Student courseStudent = new Student();

 //My solution
        courseStudent.setName("Smith");
        courseStudent.setAge(20);
        courseStudent.setID(9999);

        courseStudent.printAll();
        System.out.println(", ID: " + courseStudent.getID());


    }
}
// ===== end =====
```
# Below is my code for W7-8>4/5
```java
public class Course {
    private String courseNumber;
    private String courseTitle;

    public void setCourseNumber(String courseNumber) {
        this.courseNumber = courseNumber;
    }

    public String getCourseNumber() {
        return courseNumber;
    }

    public void setCourseTitle(String courseTitle) {
        this.courseTitle = courseTitle;
    }

    public String getCourseTitle() {
        return courseTitle;
    }

    public void PrintInfo() {
        System.out.println("Course Information:");
        System.out.println("   Course Number: " + courseNumber);
        System.out.println("   Course Title: " + courseTitle);
    }

    public static void main(String[] args) {

        Course myCourse = new Course();
        myCourse.setCourseNumber("ECE287");
        myCourse.setCourseTitle("Digital Systems Design");

        OfferedCourse myOfferedCourse = new OfferedCourse();

        myOfferedCourse.setCourseNumber("ECE387");
        myOfferedCourse.setCourseTitle("Embedded Systems Design");

        myOfferedCourse.setInstructorName("Mark Patterson");
        myOfferedCourse.setLocation("Wilson Hall 231");
        myOfferedCourse.setClassTime("WF: 2-3:30 pm");

        myCourse.PrintInfo();

        myOfferedCourse.PrintInfo();
        System.out.println("   Instructor Name: " + myOfferedCourse.getInstructorName());
        System.out.println("   Location: " + myOfferedCourse.getLocation());
        System.out.println("   Class Time: " + myOfferedCourse.getClassTime());
    }
}

class OfferedCourse extends Course {
    private String instructorName;
    private String location;
    private String classTime;
    
    public void setInstructorName(String instructorName) {
        this.instructorName = instructorName;
    }

    public String getInstructorName() {
        return instructorName;
    }

    public void setLocation(String location) {
        this.location = location;
    }

    public String getLocation() {
        return location;
    }

    public void setClassTime(String classTime) {
        this.classTime = classTime;
    }

    public String getClassTime() {
        return classTime;
    }
}
```
## Note: I enjoyed learning about inheritance. I understood it using a "parent-child" approach rather than a "base-derived" approach. Too many fancy words and I like to keep it simple.
