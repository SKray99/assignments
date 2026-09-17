# This is my W4>1/2 code:
```java
import java.util.Scanner;

public class StudentGradeToolkit {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        System.out.print("Enter student name: ");
        String name = input.nextLine();

        System.out.print("Enter score 1: ");
        double score1 = input.nextDouble();

        System.out.print("Enter score 2: ");
        double score2 = input.nextDouble();

        System.out.print("Enter score 3: ");
        double score3 = input.nextDouble();

        if (!isValidScore(score1) || !isValidScore(score2) || !isValidScore(score3)) {
            System.out.println("Error: One or more entered scores are invalid. Grades must be between 0 and 100.");
        } else {

            score1 = addBonus(score1);
            score2 = addBonus(score2);
            score3 = addBonus(score3);

            double average = calculateAverage(score1, score2, score3);
            char grade = determineGrade(average);
            boolean passing = isPassing(average);

            printReport(name, average, grade, passing);

            double high = highest(score1, score2);
            high = highest(high, score3);
            System.out.printf("Highest Score (with bonus): %.1f\n", high);
        }

        input.close();
    }

    public static boolean isValidScore(double score) {
        return score >= 0 && score <= 100;
    }

    public static double calculateAverage(double score1, double score2, double score3) {
        return (score1 + score2 + score3) / 3.0;
    }

        public static char determineGrade(double average) {
            if (average >= 90) {
                return 'A';
            } else if (average >= 80) {
                return 'B';
            } else if (average >= 70) {
                return 'C';
            } else if (average >= 60) {
                return 'D';
            } else {
                return 'F';
            }
        }
        public static boolean isPassing(double average){
            return average >= 60;
        }
    public static void printReport(String name, double average, char grade, boolean passing) {
        System.out.println("-----Student Report-----");
        System.out.println("Name: " + name);
        System.out.printf("Average: %.2f\n", average);
        System.out.println("Grade: " + grade);
        System.out.println("Status: " + (passing ? "Passing" : "Failing"));
    }

    public static double addBonus(double score) {
        double updatedScore = score + 5;
        return (updatedScore > 100) ? 100 : updatedScore;
    }

    public static double highest(double a, double b) {
        return (a > b) ? a : b;
    }
}
```
# Part 8 (Pass-by-Value questions):
### 1. What value is displayed? 80.0
### 2. Why does "testScore" remain unchanged? The score changed only within the method, but since it didn't return a value, the rest of the code didn't get a new value to add.
### 3, Below is the corrected code (added "return" and "double"):
```java
public static double addBonus(double score) {
    return score + 5;
}
```
# Part 11 (Debugging Challenge): 
### 1. Why does this method fail to compile? It doesn't compile because the code has no instruction for when "b" is greater than or equal to "a". It's incomplete.
### 2. Which execution path does not return a value? The path where "b" is greater than or equal to "a".
### 3. Below is the corrected code:
```java
public static int larger(int a, int b) {
    if (a > b) {
        return a;
    }
    return b;
}
```


