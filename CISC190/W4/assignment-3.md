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
#
#
#
#
#
# This is my W4>2/2 code
```java
import java.util.Scanner;

public class NumericToolkit {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int choice;

        do {
            displayMenu();
            choice = readChoice(input);

            switch (choice) {
                case 1:
                    handleGcd(input);
                    break;
                case 2:
                    handlePrime(input);
                    break;
                case 3:
                    handleHexConversion(input);
                    break;
                case 4:
                    handleMaximum(input);
                    break;
                case 5:
                    handleRandomCharacters();
                    break;
                default:
                    System.out.println("Thanks for stopping by! -Sage K.");
            }
            System.out.println();
        } while (choice != 0);

        input.close();
    }

    public static void displayMenu() {
        System.out.println("1. Greatest Common Divisor");
        System.out.println("2. Prime Test");
        System.out.println("3. Hexadecimal to Decimal");
        System.out.println("4. Maximum Value");
        System.out.println("5. Generate Random Characters");
        System.out.println("0. Exit");
    }

    public static int readChoice(Scanner input) {
        System.out.print("Enter your choice: ");
        return input.nextInt();
    }

    public static void handleGcd(Scanner input) {
        System.out.print("Enter first number: ");
        int first = input.nextInt();
        System.out.print("Enter second number: ");
        int second = input.nextInt();

        int result = gcd(first,second);
        System.out.println("The GCD is: " + result);
    }

    public static void handlePrime(Scanner input) {
        System.out.print("Enter an integer to test for primality: ");
        int number = input.nextInt();

        if (isPrime(number)) {
            System.out.println(number + " is a prime number.");
        } else {
            System.out.println(number + " is not a prime number.");
        }
    }

    public static void handleHexConversion(Scanner input) {
        System.out.print("Enter a hexadecimal string: ");
        String hex = input.next();

        int result = hexToDecimal(hex);
        System.out.println("The decimal value of given hex is " + result);
    }

    public static void handleMaximum(Scanner input) {
        System.out.println("Choose maximum comparison type:");
        System.out.println("1. Two integers");
        System.out.println("2. Two doubles");
        System.out.println("3. Three integers");
        System.out.print("Your choice: ");
        int type = input.nextInt();

        if (type == 1) {
            System.out.print("Enter first integer: ");
            int a = input.nextInt();
            System.out.print("Enter second integer: ");
            int b = input.nextInt();
            System.out.println("Maximum: " + max(a, b));
        } else if (type == 2) {
            System.out.print("Enter first double: ");
            double a = input.nextDouble();
            System.out.print("Enter second double: ");
            double b = input.nextDouble();
            System.out.println("Maximum: " + max(a, b));
        } else if (type == 3) {
            System.out.print("Enter first integer: ");
            int a = input.nextInt();
            System.out.print("Enter second integer: ");
            int b = input.nextInt();
            System.out.print("Enter third integer: ");
            int c = input.nextInt();
            System.out.println("Maximum: " + max(a, b, c));
        } else {
            System.out.println("Invalid maximum type choice.");
        }
    }

    public static void handleRandomCharacters() {
        System.out.println("Random Lowercase Letter: " + randomLowercaseLetter());
        System.out.println("Random Uppercase Letter: " + randomUppercaseLetter());
        System.out.println("Random Digit: "            + randomDigit());
    }

    public static int gcd(int first, int second) {
        while (second != 0) {
            int temp = second;
            second = first % second;
            first = temp;
        }
        return first;
    }
    public static boolean isPrime(int number) {
        if (number <= 1) {
            return false;
        }
        for (int i = 2; i <= Math.sqrt(number); i++) {
            if (number % i == 0) {
                return false;
            }
        }
        return true;
    }
public static int hexDigitToDecimal(char digit) {
    char upperDigit = Character.toUpperCase(digit);

    if (upperDigit >= '0' && upperDigit <= '9') {
        return upperDigit - '0';
    } else if (upperDigit >= 'A' && upperDigit <= 'F') {
        return 10 + (upperDigit - 'A');
    }
    return -1;
}
public static int hexToDecimal(String hex) {
    int decimalValue = 0;
    for (int i = 0; i < hex.length(); i++) {
        char digit = hex.charAt(i);
        int digitValue = hexDigitToDecimal(digit);
        decimalValue = decimalValue * 16 + digitValue;
    }
    return decimalValue;
}
public static int max(int a, int b) {
    if (a > b) {
        return a;
    } else {
        return b;
    }
}

public static double max(double a, double b) {
        if (a > b) {
            return a;
        } else {
            return b;
        }
}
public static int max(int a, int b, int c) {
    return max(max(a, b), c);
}

    public static char randomCharacter(char first, char last) {
        return (char) (first + Math.random() * (last - first + 1));
    }

    public static char randomLowercaseLetter() {
        return randomCharacter('a', 'z');
    }

    public static char randomUppercaseLetter() {
        return randomCharacter('A', 'Z');
    }

    public static char randomDigit() {
        return randomCharacter('0', '9');
    }
}
```
# Part 7 (Ambiguous Invocation Investigation):
### 1. Why can this be called ambiguous? Both fives are integers, and Java can convert them into doubles. It doesn't know whether to match (int, double) or (double, int), so it throws an error.
### 2. How could you modify the arguments to make the intended overload clear? Add a decimal point to specify which one of the numbers is a double.
### 3. How could you redesign the overloads to reduce ambiguity? Just create a method that takes two doubles instead, as shown below:
```java
public static double combine(double a, double b) {
    return a + b;
}
```
# Part 8 (Scope Challenge):
### 1. Why does the final statement fail? The "result" is inside the "if" section. Since it is there, the print command at the end can't find it because it's outside the curly braces.
### 2. Where does the scope of the result begin and end? It begins inside of the "if" section where it says "int result = value * 2" and it ends at the closing curly brace of the "if" section.
### 3. Below is the corrected code:
```java
public static void scopeDemo() {
    int value = 10;
    int result = 0;

    if (value > 0) {
        result = value * 2;
    }

    System.out.println(result);
}
```
# Part 12 (Method Abstraction Review):
### gcd(...): The caller needs to know the code needs two integers, and it'll return the greatest common factor. The hidden details are the math used to find the answer. 
### isPrime(...): The caller needs to know the code needs an integer and it returns true or false. The hidden detail is that the code stops at Math.sqrt.
### hexToDecimal(...): The caller needs to know the code needs a hex string and it returns a decimal number. The hidden detail is that the hexToDecimal method is deciphering the hexadecimal inputs, and it does base-16 style math.
### max(...): The caller needs to know that the code accepts numbers and it'll return the largest of them. The hidden detail is that the three-argument version also uses the two-argument version.


