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
#
#
#
#
#
# This is my W11-12>2/4 code
```java
import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class SalaryCalculatorApp {

    public static void main(String[] args) {
        JFrame frame = new JFrame("Salary");
        frame.setSize(350, 200);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(null);

        JLabel wageLabel = new JLabel("Hourly wage:");
        wageLabel.setBounds(20, 20, 100, 25);
        frame.add(wageLabel);

        JLabel salaryLabel = new JLabel("Yearly salary:");
        salaryLabel.setBounds(20, 60, 100, 25);
        frame.add(salaryLabel);

        JTextField wageField = new JTextField();
        wageField.setBounds(130, 20, 180, 25);
        frame.add(wageField);

        JTextField salaryField = new JTextField();
        salaryField.setBounds(130, 60, 180, 25);
        salaryField.setEditable(false); // Make it non-editable
        frame.add(salaryField);

        JButton calculateButton = new JButton("Calculate");
        calculateButton.setBounds(30, 110, 110, 30);
        frame.add(calculateButton);

        JButton resetButton = new JButton("Reset");
        resetButton.setBounds(190, 110, 110, 30);
        frame.add(resetButton);

        calculateButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                try {
                    String wageText = wageField.getText();
                    double hourlyWage = Double.parseDouble(wageText);

                    double yearlySalary = hourlyWage * 40 * 50;

                    salaryField.setText(String.format("$%.2f", yearlySalary));
                } catch (NumberFormatException ex) {
                    JOptionPane.showMessageDialog(frame, "Please enter valid hourly wage.", "Input Error", JOptionPane.ERROR_MESSAGE);
                }
            }
        });

        resetButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                wageField.setText("");
                salaryField.setText("");
            }
        });

        frame.setLocationRelativeTo(null);
        frame.setVisible(true);
    }
}
```
