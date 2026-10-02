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
## Part 7: Make an Independent Copy
### Explain why changing second[0] also changes scores[0]:
#### Writing double[] second = scores doesn't make a new array; it just creates a second name for the same list in memory. Because both variables point to the same numbers, changing an item using second instantly changes what scores sees.
#
#
#
#
#
# This is my Week 5-6>2/4 code
```java
import java.util.Random;
import java.util.Scanner;

public class ArrayAlgorithmToolkit {

    public static int[] getRandomData(int size, int min, int max) {
        int[] numbers = new int[size];
        Random rand = new Random();

        for (int i = 0; i < numbers.length; i++) {
            numbers[i] = rand.nextInt((max - min) + 1) + min;
        }
        return numbers;
    }

    public static void printArray(int[] values) {
        System.out.print("[ ");
        for (int index = 0; index < values.length; index++) {
            System.out.print(values[index]);
            if (index < values.length - 1) {
                System.out.print(", ");
            }
        }
        System.out.println(" ]");
    }

    public static int[] reverse(int[] values) {
        int[] result = new int[values.length];
        int targetIndex = 0;
        for (int srcIndex = values.length - 1; srcIndex >= 0; srcIndex--) {
            result[targetIndex] = values[srcIndex];
            targetIndex++;
        }
        return result;
    }
    // This sorts the array in-place, so it will change the original dataset
    public static void selectionSort(int[] values) {
        for (int startIndex = 0; startIndex < values.length - 1; startIndex++) {
            int smallestIndex = startIndex;
            for (int scanIndex = startIndex + 1; scanIndex < values.length; scanIndex++) {
                if (values[scanIndex] < values[smallestIndex]) {
                    smallestIndex = scanIndex;
                }
            }

            int temp = values[smallestIndex];
            values[smallestIndex] = values[startIndex];
            values[startIndex] = temp;
        }
    }

    public static int linearSearch(int[] values, int key) {
        for (int index = 0; index < values.length; index++) {
            if (values[index] == key) {
                return index;
            }
        }
        return -1;
    }

    public static int binarySearch(int[] values, int key) {
        int start = 0;
        int end = values.length - 1;

        while (start <= end) {
            int middle = (start + end) / 2;

            if (values[middle] == key) {
                return middle;
            } else if (values[middle] < key) {
                start = middle + 1;
            } else {
                end = middle - 1;
            }
        }
        return -1;
    }
    // This shuffles the array in-place, so it will mix up the original dataset
    public static void shuffle(int[] values) {
        Random rand = new Random();
        for (int currentIndex = values.length - 1; currentIndex > 0; currentIndex--) {
            int randomIndex = rand.nextInt(currentIndex + 1);

            int temp = values[currentIndex];
            values[currentIndex] = values[randomIndex];
            values[randomIndex] = temp;
        }
    }

    public static void main(String[] args) {
        int size = 25;

        if (args.length > 0) {
            size = Integer.parseInt(args[0]);
        }

        int[] dataset = getRandomData(size, 10, 99);
        Scanner input = new Scanner(System.in);
        int choice = -1;

        while (choice != 0) {
            System.out.println("\n 1. Display data");
            System.out.println(" 2. Reverse data");
            System.out.println(" 3. Sort using selection sort");
            System.out.println(" 4. Search using linear search");
            System.out.println(" 5. Search using binary search");
            System.out.println(" 6. Shuffle data");
            System.out.println(" 7. Regenerate data");
            System.out.println(" 0. Exit");
            System.out.print("Enter choice: ");

            choice = input.nextInt();

            if (choice == 1) {
                System.out.print("Array: ");
                printArray(dataset);

            } else if (choice == 2) {
                int[] rev = reverse(dataset);
                System.out.print("Reversed Copy: ");
                printArray(rev);

            } else if (choice == 3) {
                int[] copy = new int[dataset.length];
                for (int i = 0; i < dataset.length; i++) {
                    copy[i] = dataset[i];
                }
                java.util.Arrays.sort(copy);
                selectionSort(dataset);
                System.out.print("Sorted: ");
                printArray(dataset);

                System.out.print("\nChecking if it matches with Java utility: ");
                if (java.util.Arrays.equals(dataset, copy)) {
                    System.out.println("matched");
                } else {
                    System.out.println("Differences due to duplicate numbers handling)");
                }

            } else if (choice == 4) {
                System.out.print("Enter key: ");
                int searchKey = input.nextInt();
                int idx = linearSearch(dataset, searchKey);
                int localLinearCount = (idx == -1) ? dataset.length : (idx + 1);
                System.out.println("Found at index: " + idx + " (Comparisons: " + localLinearCount + ")");

            } else if (choice == 5) {
                System.out.print("Enter key: ");
                int searchKey = input.nextInt();
                int searchedNumber = binarySearch(dataset, searchKey);
                int localBinaryCount = 0;
                int remainingElements = dataset.length;
                while (remainingElements > 0) {
                    localBinaryCount++;
                    remainingElements = remainingElements / 2;
                }

                System.out.println("Found at index: " + searchedNumber + " (Comparisons: " + localBinaryCount + ")");

                int officialIndex = java.util.Arrays.binarySearch(dataset, searchKey);
                System.out.println("Part 7 Result: " + officialIndex );

            } else if (choice == 6) {
                shuffle(dataset);
                System.out.print("Shuffled: ");
                printArray(dataset);

            } else if (choice == 7) {
                dataset = getRandomData(size, 10, 99);
                System.out.print("New Data: ");
                printArray(dataset);

            } else if (choice == 0) {
                System.out.println("Thank you for running the program! - Sage");

            } else {
                System.out.println("Invalid choice. Try again.");
            }
        }
        input.close();
    }
}
```
