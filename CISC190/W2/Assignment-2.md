# This is my W2 assignment 

```java
// Part 1
import java.util.Scanner;

public class CourseRegistrationAdvisor {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);
        // Part 2
        System.out.println("Placement score (0-100): ");
        int placementScore = input.nextInt();
        // Part 3
        if (placementScore >= 0 && placementScore <= 100) {

            System.out.println("Prerequisites completed? (true/false)");
            boolean PrerequisiteCompleted = input.nextBoolean();

            System.out.println("Program type: ");
            System.out.println("1 - Computer Science ");
            System.out.println("2 - Data Science");
            System.out.println("3 - Information Systems");
            System.out.println("4 - Other");
            System.out.println("Enter program type (1-4): ");
            int programType = input.nextInt();

            System.out.println("Completed college units: ");
            double completedUnits = input.nextDouble();
            
            String preparationLevel;
            // Part 4
            if (placementScore >= 90) {
                preparationLevel = "Advanced";
            } else if (placementScore >= 75) {
                preparationLevel = "Ready";
            } else if (placementScore >= 60) {
                preparationLevel = "Developing";
            } else {
                preparationLevel = "Needs Preparation";
            }
            System.out.println("----- Course Registration Advisor -----");
            System.out.println(" ");
            System.out.println("Placement score: " + placementScore);
            System.out.println("Prerequisite completed: " + PrerequisiteCompleted);
            System.out.println("Preparation level: " + preparationLevel);

            // Part 5
            if (placementScore >= 75 && PrerequisiteCompleted) {
                System.out.println("Registration status: Eligible");
            } else {
                System.out.println("Registration status: Advisor review required");
            }
            // Part 6
            if (!PrerequisiteCompleted) {
                System.out.println("Guidance note: Complete the prerequisite course first.");
            } else if (placementScore < 75) {
                System.out.println("Guidance note: Additional preparation is recommended.");

            }
            // Part 7
            switch (programType) {

                case 1:
                    System.out.println("Program: Computer Science pathway");
                    break;
                case 2:
                    System.out.println("Program: Data Science pathway");
                    break;
                case 3:
                    System.out.println("Program: Information Systems pathway");
                    break;
                case 4:
                    System.out.println("Program: General elective pathway");
                    break;
                default:
                    System.out.println("Invalid program type");
            }
            // Part 8
            String studentStatus = (completedUnits < 12) ? "New Student" : "Continuing Student";
            System.out.println("Student status: " + studentStatus);

            // Part 10
            boolean earlyRegistrationPriority = PrerequisiteCompleted && ((completedUnits >= 30 && placementScore >= 75) || completedUnits >= 60);
            System.out.println("Early Registration Priority: " + earlyRegistrationPriority);



        } else {System.out.println("Invalid placement score."); }

    }
}
```
