# This is my W10>1/1 code:
```java
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class PhotoOrganizer {

    public static void main(String[] args) {

        Scanner consoleScanner = new Scanner(System.in);
        System.out.print("Enter the file name: ");
        String inputFileName = consoleScanner.nextLine();

        try {
            File inputFile = new File(inputFileName);
            Scanner fileScanner = new Scanner(inputFile);

            while (fileScanner.hasNextLine()) {
                String fileName = fileScanner.nextLine();

                if (!fileName.trim().isEmpty()) {
                    String changedFileName = fileName.replace("_photo.jpg", "_info.txt");

                    System.out.println(changedFileName);
                }
            }

            fileScanner.close();

        } catch (FileNotFoundException e) {
            System.out.println("Error: The file '" + inputFileName + "' was not found.");
        } finally {
            consoleScanner.close();
        }
    }
}
```
#
#
#
#
#
# NO MORE ENTRIES FOR THIS ASSIGNMENT
