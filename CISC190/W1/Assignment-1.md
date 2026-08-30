# This is my W1-1/4 code

```java
// Class declaration  // Opening brace
public class CourseIntroduction {
    // Main method               // Opening brace
    public static void main(String[] args) {
        // Output statements  // String literals  // Semicolons
        System.out.println("This is me adding another statement.");
        System.out.println("Course: Java Programming (This is me changing text in a string literal)");
        System.out.println("Goal: I want to build a stronger foundation in programming.");
        System.out.println();
        System.out.println("Name: Sage Kray");

    } // Closing brace
} // Closing brace
```
#
#
#
# This is my W1-2/4 code

## Below is my JavaProcess.java file
```java
public class JavaProcess {

    public static void main(String[] args) {

        System.out.println("I understand the Java compilation process.");
    }
}
```

## Below is my CompilationSteps.java file
```java
public class CompilationSteps {
    public static void main(String[] args) {
        System.out.println("Step 1: Write Java source code.");
        System.out.println("Step 2: Compile the source code using javac.");
        System.out.println("Step 3: The compiler generates Java bytecode.");
        System.out.println("Step 4: The JVM executes the bytecode.");
    }
}
```
### Java source file: Contains text code written by the programmer.
### Java Compiler: Converts code into machine code.
### Bytecode: Translated code that a computer can read.
### JVM: The engine that runs the code on the computer.
#
#
#
# This is my W1-3/4 code

## Part 1: Syntax Errors
```java
public class SyntaxPractice {

    public static void main(String[] args) {
        System.out.println("Learning Java");
        System.out.println("Finding errors is an important skill");
    }
}
// First error found was the missing semicolon.
// Second error found was the missing closing quotation.
```
### 1. I identified 2 errors.
### 2. The second statement involved a missing statement terminator.
### 3. The first statement involved a string literal.
### 4. No, the compiler did not always point to the actual cause.

## Part 2: Another Syntax Challenge
```java
public class StudentMessage {

    public static void main(String[] args) {
        System.out.println("Welcome to the course!");
        System.out.println("Practice Java every week.");
    }
}
// First error was the opening brace
// Second error was the missing semicolon
```

## Part 3: Runtime Error
```java
public class RuntimePractice {

    public static void main(String[] args) {
        int number = 10;
        int divisor = 2;

        System.out.println(number / divisor);
    }
}
```

## Part 4: Logic Error
```java
public class TemperaturePractice {

    public static void main(String[] args) {
        double celsius = 35;
        double fahrenheit = (9.0 / 5.0) * celsius + 32;

        System.out.println("Celsius: " + celsius);
        System.out.println("Fahrenheit: " + fahrenheit);
    }
}
// First run: 35.0 degrees Celsius, 67.0 degrees Fahrenheit
// Second run: 35.0 degrees Celsius, 95.0 degrees Fahrenheit
```
## Part 5: Classify the Errors
### Scenario A: Syntax (missing semicolon)
### Scenario B: Logic
### Scenario C: Runtime (division by zero)
### Scenario D: Syntax (missing closing quotation)
### Scenario E: Logic

## Part 6: Final Debugging Challenge
```java
public class StudentAverage {

    public static void main(String[] args) {

        String studentName = "Jordan";
        double score1 = 80;
        double score2 = 90;

        double average = (score1 + score2) / 2;

        System.out.println("Student: " + studentName);
        System.out.println("Average: " + average);
    }
}

// Fixed by adding a semicolon and parentheses to the addition of both scores.
```
