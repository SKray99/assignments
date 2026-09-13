# This is my W2-3-1/2 code

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
# Part 11:
### What will the program display for a score of 95? It will display "D".
### Why is the result incorrect? Because the first line of code is ">= 60", the program will see it as true and bypass the rest of the code. It should be from highest to lowest score.
### The code should look like this:
```java
double score = 95;

if (score >= 90) {
    System.out.println("A");
}
else if (score >= 80) {
    System.out.println("B");
}
else if (score >= 70) {
    System.out.println("C");
}
else if (score >= 60) {
    System.out.println("D");
}
```
# Part 12:
### Will the message be displayed? Yes, the message will be displayed, but not as intended.
### What is wrong with the "if" statement? It has a semicolon, which acts as a period and terminates it before it can even affect the next line of code.
### Why can this mistake be difficult to detect? The code works but not as intended. We won't see any errors, and the code will run through, which makes it hard to detect.
#
#
#
#
#
# This is my W2-3-2/2 code

```java
import java.util.Scanner;

public class ScoreAnalyzer {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        // Part 2
        int validScores = 0;
        double totalValidScores = 0.0;
        int passingScores = 0;
        int scoresBelow60 = 0;
        double highestScore = 0.0;
        double lowestScore = 0.0;

        // Part 3
        System.out.print("Enter a score from 0 to 100 (-1 to finish): ");
        double score = input.nextDouble();

        while (score != -1) {
            // Part 4
            if (score >= 0 && score <= 100) {
                // Part 5
                validScores++;
                totalValidScores += score;
                // Part 6
                if (validScores == 1) {
                    highestScore = score;
                    lowestScore = score;
                } else {
                    if (score > highestScore) {
                        highestScore = score;
                    }

                    if (score < lowestScore) {
                        lowestScore = score;
                    }
                }

                // Part 7
                if (score >= 60) {
                    passingScores++;
                } else {
                    scoresBelow60++;
                }
            } else {
                System.out.println("Invalid score. Value ignored.");
            }

            System.out.print("Enter a score from 0 to 100 (-1 to finish): ");
            score = input.nextDouble();
        }
        // Part 8
        System.out.println("----- Score Summary -----");
        System.out.println("Valid scores: " + validScores);
        
        if (validScores > 0) {
            double average = totalValidScores / validScores;
            System.out.printf("Average: %.2f\n", average);
            System.out.printf("Highest: %.2f\n", highestScore);
            System.out.printf("Lowest: %.2f\n", lowestScore);
        } else {
            System.out.println("Average: ");
        }
        System.out.println("Passing scores: " + passingScores);
        System.out.println("Below 60 scores: " + scoresBelow60);

    }
}
```
# Part 9 (converting one section to a do-while loop):

```java
import java.util.Scanner;

public class ScoreAnalyzerDoWhile {

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        // Part 2
        int validScores = 0;
        double totalValidScores = 0.0;
        int passingScores = 0;
        int scoresBelow60 = 0;
        double highestScore = 0.0;
        double lowestScore = 0.0;

        // Part 3
        double score;

        do {
            System.out.print("Enter a score from 0 to 100 (-1 to finish): ");
            score = input.nextDouble();

            if (score != -1) {

                // Part 4
                if (score >= 0 && score <= 100) {
                    // Part 5
                    validScores++;
                    totalValidScores += score;
                    // Part 6
                    if (validScores == 1) {
                        highestScore = score;
                        lowestScore = score;
                    } else {
                        if (score > highestScore) {
                            highestScore = score;
                        }

                        if (score < lowestScore) {
                            lowestScore = score;
                        }
                    }

                    // Part 7
                    if (score >= 60) {
                        passingScores++;
                    } else {
                        scoresBelow60++;
                    }
                } else {
                    System.out.println("Invalid score. Value ignored.");
                }

                System.out.print("Enter a score from 0 to 100 (-1 to finish): ");
                score = input.nextDouble();
            }
        } while (score != -1);

        System.out.println("----- Score Summary -----");
        System.out.println("Valid scores: " + validScores);

        if (validScores > 0) {
            double average = totalValidScores / validScores;
            System.out.printf("Average: %.2f\n", average);
            System.out.printf("Highest: %.2f\n", highestScore);
            System.out.printf("Lowest: %.2f\n", lowestScore);
        } else {
            System.out.println("Average: ");
        }
        System.out.println("Passing scores: " + passingScores);
        System.out.println("Below 60 scores: " + scoresBelow60);


    }
}
```
# Part 10 (Use a loop for a fixed number of scores):

```java
import java.util.Scanner;

public class FixedScoreAnalyzer {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        double total = 0.0;

        System.out.println("Enter 5 scores! ");

        for (int i = 1; i <= 5; i++) {
            System.out.print("Enter score #" + i + ":" );
            double score = input.nextDouble();
            total += score;
        }
        double average = total / 5;

        System.out.println("----- Results -----");
        System.out.printf("Total: %.2f\n", total);
        System.out.printf("Average: %.2f\n", average);
    }
}
```
# Part 11 (Nested loop challenge):

```java
public class ScorePattern {

    public static void main(String[] args) {

        for (int row = 1; row <= 5; row++) {

            for (int column = 1; column <= row; column++) {
                System.out.print(column + " ");
            }
            System.out.println();
        }
    }
}
```
# Part 12 (Break challenge):

```java
public class Part12BreakChallenge {
    public static void main(String[] args) {

        for (int i = 1; i <= 100; i++) {
            if (i > 20 && i % 4 == 0 && i % 7 == 0) {
                System.out.println("First # greater than 20 and divisible by both 4 and 7: " + i);

                break;
            }
        }
    }
}
```
# Part 13 (Continue challenge):

```java
public class Part13ContinueChallenge {
    public static void main(String[] args) {

        for (int i = 1; i <= 20; i++) {
            if (i % 3 == 0) {
                continue;
            }
            System.out.print(i + " ");
        }
        System.out.println();
    }
}
```
# Part 14:
### Why does the loop never terminate? The value "1" is never changing, so the count stays the same since 1 <= 5.
### Which statement is missing? The counter is missing (count++)
### Below is the corrected loop:

```java
int count = 1;

while (count <= 5) {
        System.out.println(count); count++;
        }
```

# Part 15 (Debugging challenge-- off-by-one error)
### What is the last number displayed? 9
### Why is "10" missing? The code has the loop i < 10, not i <= 10, which means it's not accounting for 10.
### Below is the corrected loop condition:

```java
for (int i = 1; i <= 10; i++) {
    System.out.println(i);
}
```

# Part 16 (Debugging challenge -- Semicolon error)
### What is wrong with the loop header? There is a semicolon at the end of the "for" line and disregards the loop body five times.
### How many times does the block execute? Once since the System.out.println("Java"); is a standalone code outside of the loop.
### Below is the corrected code:

```java
for (int i = 0; i < 5; i++)
{
    System.out.println("Java");
}
```

# Part 17 (Loop section):
### Print a message exactly 20 times: **for**
### Read values until the user enters -1: **while**
### Display a menu at least once and repeat until Exit is selected: **do-while**
### Generate the first 10 multiples of 7: **for**


