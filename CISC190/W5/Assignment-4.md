# This is my Week 5-6>1/4 code
```java
import java.util.Scanner;

public class AssessmentAnalyzer {

    public static void main(String[] args) {
        double[] scores = new double[10];
        Scanner input = new Scanner(System.in);

        System.out.println("Please enter 10 assessment scores (0 to 100):");

        for (int i = 0; i < scores.length; i++) {
            boolean isValid = false;
            while (isValid == false) {
                System.out.print("Enter score " + (i + 1) + ": ");
                double userScore = input.nextDouble();

                if (userScore >= 0 && userScore <= 100) {
                    scores[i] = userScore;
                    isValid = true;
                } else {
                    System.out.println("Invalid score. Please enter a value between 0 and 100.");
                }
            }
        }

        printScores(scores);
        System.out.println();
        System.out.println("Number of Scores: " + scores.length);

        double avg = scoreAverage(scores);
        System.out.println("Average: " + avg);

        double minimumScore = minimum(scores);
        double maximumScore = maximum(scores);
        System.out.println("Minimum: " + minimumScore);
        System.out.println("Maximum: " + maximumScore);

        int standardCount = countAboveAverage(scores, avg);
        System.out.println("Above average: " + standardCount);

        System.out.println();
        System.out.print("Enter a score to search for: ");
        double searchTarget = input.nextDouble();

        int position = linearSearch(scores, searchTarget);
        if (position != -1) {
            System.out.println("Score found at index: " + position);
        } else {
            System.out.println("Score not found in the array (returned -1).");
        }

        System.out.println();
        System.out.println("--- Independent Copy ---");
        double[] myNewCopy = copyArray(scores);
        System.out.println("Changing index 0 in the copied array to 100...");

        myNewCopy[0] = 100.0;
        System.out.println("Original array at index 0: " + scores[0]);
        System.out.println("Copied array at index 0:   " + myNewCopy[0]);

        System.out.println();
        System.out.println("--- Circular Left Shift ---");
        System.out.println("Array BEFORE shift:");
        printScores(scores);

        shiftLeft(scores);

        System.out.println();
        System.out.println("Array AFTER shift:");
        printScores(scores);

        input.close();
    }

    public static void printScores(double[] scores) {
        System.out.println("--- Assessment Scores ---");
        for (int i = 0; i < scores.length; i++) {
            System.out.println("Index [" + i + "] : " + scores[i]);
        }
    }

    public static double scoreAverage(double[] scores) {
        double total = 0;
        for (int i = 0; i < scores.length; i++) {
            total = total + scores[i];
        }
        return total / scores.length;
    }

    public static double minimum(double[] scores) {
        double currentMin = scores[0];
        for (int i = 1; i < scores.length; i++) {
            if (scores[i] < currentMin) {
                currentMin = scores[i];
            }
        }
        return currentMin;
    }

    public static double maximum(double[] scores) {
        double currentMax = scores[0];
        for (int i = 1; i < scores.length; i++) {
            if (scores[i] > currentMax) {
                currentMax = scores[i];
            }
        }
        return currentMax;
    }

    public static int countAboveAverage(double[] scores, double average) {
        int counter = 0;
        for (int i = 0; i < scores.length; i++) {
            if (scores[i] > average) {
                counter++;
            }
        }
        return counter;
    }

    public static int linearSearch(double[] scores, double target) {
        for (int i = 0; i < scores.length; i++) {
            if (scores[i] == target) {
                return i;
            }
        }
        return -1;
    }

    public static double[] copyArray(double[] source) {
        double[] backup = new double[source.length];
        for (int i = 0; i < source.length; i++) {
            backup[i] = source[i];
        }
        return backup;
    }

    public static void shiftLeft(double[] scores) {
        double temp = scores[0];
        for (int i = 0; i < scores.length - 1; i++) {
            scores[i] = scores[i + 1];
        }
        scores[scores.length - 1] = temp;
    }
}
```
