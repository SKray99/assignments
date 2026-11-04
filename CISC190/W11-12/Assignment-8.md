# This is my W11-12>1/4 code
```java
import javax.swing.JFrame;
import javax.swing.JTextField;

public class SalaryGUI {
    public static void main(String[] args) {
        int hourlyWage;
        JFrame topFrame = null;
        JTextField outputField = null;

        hourlyWage = 80;

        outputField = new JTextField();

        outputField.setText("An hourly wage of " + hourlyWage + "/hr" +
                " yields $" + (hourlyWage * 40 * 50) + "/yr.");

        outputField.setEditable(false);

        topFrame = new JFrame("Salary");

        topFrame.add(outputField);

        topFrame.pack();

        topFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        topFrame.setVisible(true);
    }
}
```
## The output of this code is: An hourly wage of 80/hr yields $160000/yr.
