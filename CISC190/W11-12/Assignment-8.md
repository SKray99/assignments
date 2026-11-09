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
#
#
#
#
#
# Below is the edited code for W11-12>3/4
```java
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JSpinner;
import javax.swing.JTextField;
import javax.swing.SpinnerNumberModel;
import javax.swing.event.ChangeEvent;
import javax.swing.event.ChangeListener;

public class DogYearsFrame extends JFrame implements ChangeListener {
    private JSpinner yearsSpinner;    // Triggers travel time calculation
    private JTextField ageHumanField; // Displays dog's age in human years
    private JLabel yearsLabel;        // Label for dog years
    private JLabel ageHumanLabel;     // Label for human years

    /* Constructor creates GUI components and adds GUI components
       using a GridBagLayout. */
    DogYearsFrame() {
        double initYear;     // Spinner initial value display
        double minYear;      // Spinner min value
        double maxYear;      // Spinner max value
        double stepVal;      // Spinner step

        initYear = 0.0;
        minYear = 0.0;
        maxYear = 30.0;
        stepVal = 0.5;       // Step increment set to 0.5

        // Used to specify GUI component layout
        GridBagConstraints layoutConst = null;

        // Specifies the types of values displayed in spinner
        SpinnerNumberModel spinnerModel = null;

        // Set frame's title
        setTitle("Dog's age in human years");

        // Create labels
        yearsLabel = new JLabel("Select dog's age (years):");
        ageHumanLabel = new JLabel("Age (human years):");

        // Create a spinner model, the spinner, and set the change listener
        spinnerModel = new SpinnerNumberModel(initYear, minYear, maxYear, stepVal);
        yearsSpinner = new JSpinner(spinnerModel);
        yearsSpinner.addChangeListener(this);

        // Create field
        ageHumanField = new JTextField(15);
        ageHumanField.setEditable(false);
        ageHumanField.setText("0 - 15");

        // Use a GridBagLayout
        setLayout(new GridBagLayout());

        // Specify component's grid location
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 10, 1);
        layoutConst.anchor = GridBagConstraints.LINE_END;
        layoutConst.gridx = 0;
        layoutConst.gridy = 0;
        add(yearsLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 1, 10, 10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 0;
        add(yearsSpinner, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 10, 1);
        layoutConst.anchor = GridBagConstraints.LINE_END;
        layoutConst.gridx = 0;
        layoutConst.gridy = 1;
        add(ageHumanLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 1, 10, 10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 1;
        add(ageHumanField, layoutConst);
    }

    @Override
    public void stateChanged(ChangeEvent event) {
        Double dogAgeYears;

        dogAgeYears = (Double) yearsSpinner.getValue();

        int ageInHalves = (int) (dogAgeYears * 2);

        switch (ageInHalves) {
            case 0:
                ageHumanField.setText("0 - 15");
                break;

            case 1:
                ageHumanField.setText("7.5");
                break;

            case 2:
                ageHumanField.setText("15");
                break;

            case 3:
                ageHumanField.setText("19.5");
                break;

            case 4:
                ageHumanField.setText("24");
                break;

            case 5:
                ageHumanField.setText("26.0");
                break;

            case 6:
                ageHumanField.setText("28");
                break;

            case 7:
                ageHumanField.setText("30.0");
                break;

            case 8:
                ageHumanField.setText("32");
                break;

            case 9:
                ageHumanField.setText("34.5");
                break;

            case 10:
                ageHumanField.setText("37");
                break;

            case 11:
                ageHumanField.setText("39.5");
                break;

            case 12:
                ageHumanField.setText("42");
                break;

            case 13:
                ageHumanField.setText("44.5");
                break;

            case 14:
                ageHumanField.setText("47");
                break;

            case 15:
                ageHumanField.setText("49.5");
                break;

            case 16:
                ageHumanField.setText("52");
                break;

            case 17:
                ageHumanField.setText("54.5");
                break;

            case 18:
                ageHumanField.setText("57");
                break;

            case 19:
                ageHumanField.setText("59.5");
                break;

            case 20:
                ageHumanField.setText("62");
                break;

            case 21:
                ageHumanField.setText("64.5");
                break;

            case 22:
                ageHumanField.setText("67");
                break;

            case 23:
                ageHumanField.setText("69.5");
                break;

            case 24:
                ageHumanField.setText("72");
                break;

            case 25:
                ageHumanField.setText("74.5");
                break;

            case 26:
                ageHumanField.setText("77");
                break;

            case 27:
                ageHumanField.setText("79.5");
                break;

            case 28:
                ageHumanField.setText("82");
                break;

            default:
                ageHumanField.setText("That's a long life!");
        }
    }

    public static void main(String[] args) {

        DogYearsFrame myFrame = new DogYearsFrame();

        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}
```
