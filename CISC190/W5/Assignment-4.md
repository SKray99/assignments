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

    // This swaps the first two items in-place, changing the original dataset
    public static void swapFirstTwo(int[] values) {
        if (values.length >= 2) {
            int temp = values[0];
            values[0] = values[1];
            values[1] = temp;
        }
    }

    public static double average(int... values) {
        if (values.length == 0) {
            return 0.0;
        }
        double sum = 0;
        for (int index = 0; index < values.length; index++) {
            sum += values[index];
        }
        return sum / values.length;
    }

    public static int countOccurrences(int[] values, int key) {
        int count = 0;
        for (int index = 0; index < values.length; index++) {
            if (values[index] == key) {
                count++;
            }
        }
        return count;
    }

    public static void reportDuplicates(int[] values) {
        int[] sortedCopy = new int[values.length];
        for (int index = 0; index < values.length; index++) {
            sortedCopy[index] = values[index];
        }

        selectionSort(sortedCopy);
        System.out.println("--- Part 12: Duplicate Analysis Report ---");

        boolean foundDuplicate = false;
        int checkIndex = 0;
        while (checkIndex < sortedCopy.length) {
            int currentVal = sortedCopy[checkIndex];
            int frequency = countOccurrences(values, currentVal);

            if (frequency > 1) {
                System.out.println("Number " + currentVal + " appears " + frequency + " times.");
                foundDuplicate = true;
            }
            checkIndex = checkIndex + frequency;
        }

        if (!foundDuplicate) {
            System.out.println("No duplicate values found in the dataset.");
        }
    }

    public static void main(String[] args) {
        int size = 25;

        if (args.length > 0) {
            size = Integer.parseInt(args[0]);
        }

        int[] dataset = getRandomData(size, 10, 99);
        System.out.println("--- Part 9: Array Reference Experiment ---");
        System.out.print("Before swapFirstTwo: ");
        printArray(dataset);

        swapFirstTwo(dataset);

        System.out.print("After swapFirstTwo:  ");
        printArray(dataset);
        System.out.println("");
        System.out.println("*** I didn't know how you'd want to see Part 9 while adhering to Part 11, so I added it above - Sage ***");

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
                System.out.println("--- Part 10: Varargs Calculation ---");
                double overallAvg = average(dataset);
                System.out.println("Average of the entire dataset: " + overallAvg);

            } else if (choice == 2) {
                int[] rev = reverse(dataset);
                System.out.print("Reversed Copy: ");
                printArray(rev);

            } else if (choice == 3) {
                reportDuplicates(dataset);
                System.out.println("");
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
                System.out.println("Part 7 Verification: " + officialIndex );

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
### Note: There was nothing in our lecture material regarding duplicates. I used a YouTube video by SDET-QA and AI to teach me how to find duplicates in an array to complete Part 12. 
#
#
#
#
#
# This is my Week 5-6>3/4 code
```java
import java.util.Scanner;

public class StoreSalesAnalyzer {

    public static void main(String[] args) {

        double[][] sales = new double[4][7];
        Scanner scanner = new Scanner(System.in);

        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                double input = -1;
                while (input < 0) {
                    System.out.print("Enter sales for store " + (store + 1) + ", day " + (day + 1) + ": ");
                    input = scanner.nextDouble();
                    if (input < 0) {
                        System.out.println("Sales cannot be negative, try again.");
                    }
                }
                sales[store][day] = input;
            }
        }
        System.out.println();

        System.out.println("---Sales Matrix---");
        printSales(sales);
        System.out.println();

        System.out.println("---Sales Report---");
        System.out.println("Overall Total Weekly Sales: $" + totalSales(sales));
        System.out.println("Average Sales Amount Per Entry: $" + averageSales(sales));

        System.out.println("\n--- Breakdowns by Store ---");
        for (int store = 0; store < sales.length; store++) {
            System.out.println("Total Sales for Store " + (store + 1) + ": $" + rowTotal(sales, store));
        }

        System.out.println("\n--- Breakdowns by Day ---");
        int maxDays = getMaxColumns(sales);
        for (int day = 0; day < maxDays; day++) {
            System.out.println("Total Sales for Day " + (day + 1) + ": $" + columnTotal(sales, day));
        }

        int bestStoreIdx = bestStore(sales);
        System.out.println("\nBest-Performing Location: Store " + (bestStoreIdx + 1));

        double maxVal = findMaximum(sales);
        int[] maxPos = findMaximumPosition(sales);
        System.out.println("Largest Recorded Sale: $" + maxVal +
                " (Located at Store " + (maxPos[0] + 1) + ", Day " + (maxPos[1] + 1) + ")");
        System.out.println();

        System.out.println("---Ragged Array Results---");
        double[][] irregularSales = {
                {120.0, 145.0, 160.0},
                {90.0, 105.0},
                {200.0, 210.0, 220.0, 230.0},
                {75.0}
        };

        System.out.println("---Irregular Sales Matrix---");
        printSales(irregularSales);
        System.out.println();

        System.out.println("Irregular Array Total Sales: $" + totalSales(irregularSales));
        System.out.println("Irregular Array Average Sales: $" + averageSales(irregularSales));

        System.out.println("\n--- Irregular Breakdowns by Day ---");
        int maxIrregularDays = getMaxColumns(irregularSales);
        for (int day = 0; day < maxIrregularDays; day++) {
            System.out.println("Total Sales for Day " + (day + 1) + ": $" + columnTotal(irregularSales, day));
        }

        scanner.close();
    }

    public static void printSales(double[][] sales) {
        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                System.out.print(sales[store][day] + "\t");
            }
            System.out.println();
        }
    }

    public static double totalSales(double[][] sales) {
        double total = 0.0;
        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                total += sales[store][day];
            }
        }
        return total;
    }

    public static double averageSales(double[][] sales) {
        double total = totalSales(sales);
        int entryCount = 0;
        for (int store = 0; store < sales.length; store++) {
            entryCount += sales[store].length;
        }
        return entryCount == 0 ? 0.0 : total / entryCount;
    }

    public static double rowTotal(double[][] sales, int storeIndex) {
        double total = 0.0;
        for (int day = 0; day < sales[storeIndex].length; day++) {
            total += sales[storeIndex][day];
        }
        return total;
    }

    public static double columnTotal(double[][] sales, int dayIndex) {
        double total = 0.0;
        for (int store = 0; store < sales.length; store++) {
            if (dayIndex < sales[store].length) {
                total += sales[store][dayIndex];
            }
        }
        return total;
    }

    public static int getMaxColumns(double[][] sales) {
        int maxCols = 0;
        for (int store = 0; store < sales.length; store++) {
            if (sales[store].length > maxCols) {
                maxCols = sales[store].length;
            }
        }
        return maxCols;
    }

    public static int bestStore(double[][] sales) {
        int bestStoreIndex = 0;
        double maxTotal = rowTotal(sales, 0);

        for (int store = 1; store < sales.length; store++) {
            double currentTotal = rowTotal(sales, store);
            if (currentTotal > maxTotal) {
                maxTotal = currentTotal;
                bestStoreIndex = store;
            }
        }
        return bestStoreIndex;
    }

    public static double findMaximum(double[][] sales) {
        double max = sales[0][0];
        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                if (sales[store][day] > max) {
                    max = sales[store][day];
                }
            }
        }
        return max;
    }

    public static int[] findMaximumPosition(double[][] sales) {
        double max = sales[0][0];
        int maxStore = 0;
        int maxDay = 0;

        for (int store = 0; store < sales.length; store++) {
            for (int day = 0; day < sales[store].length; day++) {
                if (sales[store][day] > max) {
                    max = sales[store][day];
                    maxStore = store;
                    maxDay = day;
                }
            }
        }

        return new int[]{maxStore, maxDay};
    }
}
```
# Part 9:
## matrix[row].length is supposed to count how many items are in each individual row. If you don't use it, the code will fail because the program won't read uneven or ragged rows. It could crash or entirely miss data it was meant to capture.
#
# Part 10 (Debugging):
```java
for (int row = 0; row < sales.length; row++) {
    for (int column = 0; column < sales.length; column++) {
        System.out.println(sales[row][column]);
    }
}
```
## 1. What assumption does the inner loop make? The inner loop assumes the table is a perfect square because it uses sales.length rather than sales[row].length.
## 2. Why could this fail for a non-square matrix? It could crash or miss data, as explained in my part 9 question. 
## 3. Corrected loop condition below.
```java
for (int row = 0; row < sales.length; row++) {
    for (int column = 0; column < sales[row].length; column++) {
        System.out.println(sales[row][column]);
    }
}
```
