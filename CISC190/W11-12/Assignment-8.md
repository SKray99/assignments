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
#
#
#
#
#
# Below is the edited code for W11-12>4/4
```java
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.text.NumberFormat;
import java.util.ArrayList;
import javax.swing.JButton;
import javax.swing.JFormattedTextField;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JTable;
import javax.swing.JTextField;

public class SeatReservationFrame extends JFrame implements ActionListener {
    private JTextField firstNameField;             // Holds first name
    private JTextField lastNameField;              // Holds last name
    private JFormattedTextField seatNumField;      // Holds seat number
    private JFormattedTextField amountPaidField;   // Holds ticket cost
    private JLabel tableLabel;                     // Label for table display
    private JLabel seatNumLabel;                   // Label for seat number
    private JLabel firstNameLabel;                 // Label for first name
    private JLabel lastNameLabel;                  // Label for last name
    private JLabel amountPaidLabel;                // Label for amount paid
    private JButton reserveButton;                 // Triggers seat reservation
    private JButton deleteButton;                  // Triggers seat deletion
    private JButton quitButton;                    // Triggers termination of GUI
    private JTable seatStatusTable;                // Table tracks seat reservations
    private final static int NUM_SEATS = 5;        // Number of seat in reservation system
    private static ArrayList<SeatInfo> seatResArr; // ArrayList of Seat objects

    /* Constructor creates GUI components and adds GUI components
       using a GridBagLayout. */
    SeatReservationFrame() {
        Object[][] tableVals = new Object[5][4];                // Seat reservation table
        String[] columnHeadings = {"Seat Number", "First Name", // Column headings for reservation table
                "Last Name", "Amount Paid"};
        GridBagConstraints layoutConst = null;                  // GUI component layout
        NumberFormat currencyFormat = null;                     // Format for amount paid

        // Set frame's title
        setTitle("Seat reservation");

        // Add 5 seat objects to ArrayList
        seatResArr = new ArrayList<SeatInfo>();
        seatsAddElements(seatResArr, NUM_SEATS);

        // Make all seats empty
        seatsMakeEmpty(seatResArr);

        // Create seat reservation table
        tableLabel = new JLabel("Seat reservation status:");
        seatNumLabel = new JLabel("Seat Number:");
        firstNameLabel = new JLabel("First Name:");
        lastNameLabel = new JLabel("Last Name:");
        amountPaidLabel = new JLabel("Amount Paid:");

        seatNumField = new JFormattedTextField(NumberFormat.getIntegerInstance());
        seatNumField.setEditable(true);
        seatNumField.setValue(0);

        firstNameField = new JTextField(20);
        firstNameField.setEditable(true);
        firstNameField.setText("John");

        lastNameField = new JTextField(20);
        lastNameField.setEditable(true);
        lastNameField.setText("Doe");

        currencyFormat = NumberFormat.getCurrencyInstance();
        currencyFormat.setMaximumFractionDigits(0);
        amountPaidField = new JFormattedTextField(currencyFormat);
        amountPaidField.setEditable(true);
        amountPaidField.setValue(0.0);

        reserveButton = new JButton("Reserve");
        reserveButton.addActionListener(this);

        deleteButton = new JButton("Delete");
        deleteButton.addActionListener(this);

        quitButton = new JButton("Quit");
        quitButton.addActionListener(this);

        // Initialize table
        seatStatusTable = new JTable(tableVals, columnHeadings);
        seatStatusTable.setEnabled(false); // Prevent user input via table

        // Add components using GridBagLayout
        setLayout(new GridBagLayout());

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 1, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 0;
        layoutConst.gridy = 0;
        add(tableLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1, 10, 0, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 0;
        layoutConst.gridy = 1;
        layoutConst.gridwidth = 4;
        add(seatStatusTable.getTableHeader(), layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(0, 10, 10, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 0;
        layoutConst.gridy = 2;
        layoutConst.gridwidth = 4;
        add(seatStatusTable, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 1, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 0;
        layoutConst.gridy = 3;
        add(seatNumLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1, 10, 10, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 0;
        layoutConst.gridy = 4;
        add(seatNumField, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 1, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 3;
        add(firstNameLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1, 10, 10, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 4;
        add(firstNameField, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 1, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 2;
        layoutConst.gridy = 3;
        add(lastNameLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1, 10, 10, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 2;
        layoutConst.gridy = 4;
        add(lastNameField, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 1, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 3;
        layoutConst.gridy = 3;
        add(amountPaidLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1, 10, 10, 0);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 3;
        layoutConst.gridy = 4;
        add(amountPaidField, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(0, 10, 10, 5);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 4;
        layoutConst.gridy = 4;
        add(reserveButton, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(0, 10, 10, 5);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 4;
        layoutConst.gridy = 5;
        add(deleteButton, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(0, 5, 10, 10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 5;
        layoutConst.gridy = 5;
        add(quitButton, layoutConst);
    }

    /* Called when either button is pressed. */
    @Override
    public void actionPerformed(ActionEvent event) {
        SeatInfo seatElement;  // Seat information
        String firstName;      // First name
        String lastName;       // Last name
        int seatNum;           // Seat number
        int amtPaid;           // Amount paid

        // Get source of event (3 buttons in GUI)
        JButton sourceEvent = (JButton) event.getSource();

        // User pressed the reserve button
        if (sourceEvent == reserveButton) {
            seatNum = ((Number) seatNumField.getValue()).intValue();

            // User tried to reserve non-existing seat
            if (seatNum < 0 || seatNum >= NUM_SEATS) {
                // Show failure dialog
                JOptionPane.showMessageDialog(this, "Seat doesn't exist!");
            }
            // User tried to reserve a non-empty seat
            else if (!(seatResArr.get(seatNum).isEmpty())) {
                // Show failure dialog
                JOptionPane.showMessageDialog(this, "Seat is not empty!");
            }
            // Reserve the specified seat
            else {
                firstName = firstNameField.getText();
                lastName = lastNameField.getText();
                amtPaid = ((Number) amountPaidField.getValue()).intValue();

                seatElement = new SeatInfo();         // Create new Seat object
                seatElement.reserveSeat(firstName, lastName, amtPaid);
                seatResArr.set(seatNum, seatElement); // Add seat to ArrayList

                updateTable();                        // Synchronize table with seatResArr ArrayList

                // Show success dialog
                JOptionPane.showMessageDialog(this, "Seat reservation completed.");
            }
        }
        else if (sourceEvent == deleteButton) {
            seatNum = ((Number) seatNumField.getValue()).intValue();

            if (seatNum < 0 || seatNum >= NUM_SEATS) {
                JOptionPane.showMessageDialog(this, "Seat doesn't exist!");
            }
        else if (seatResArr.get(seatNum).isEmpty()) {
            JOptionPane.showMessageDialog(this, "Seat is already empty!");
        }
        else {
            seatResArr.get(seatNum).makeEmpty();
            updateTable();
            JOptionPane.showMessageDialog(this, "User deleted successfully.");
        }
    }
        else if (sourceEvent == quitButton) {
        dispose();                               // Terminate program
    }
} // This correctly closes the actionPerformed method

/* Updates the reservation information displayed by the table */
public void updateTable() {
    final int seatNumCol = 0;   // Col num for seat numbers
    final int firstNameCol = 1; // Col num for first names
    final int lastNameCol = 2;  // Col num for last names
    final int paidCol = 3;      // Col num for amount paid
    int i;                      // Loop index

    for (i = 0; i < NUM_SEATS && i < seatResArr.size(); ++i) {
        if (seatResArr.get(i).isEmpty()) { // Clear table entries
            seatStatusTable.setValueAt(null, i, seatNumCol);
            seatStatusTable.setValueAt(null, i, firstNameCol);
            seatStatusTable.setValueAt(null, i, lastNameCol);
            seatStatusTable.setValueAt(null, i, paidCol);
        }
        else {                             // Update table with content in the seatResArr ArrayList
            seatStatusTable.setValueAt(i, i, seatNumCol);
            seatStatusTable.setValueAt(seatResArr.get(i).getFirstName(), i, firstNameCol);
            seatStatusTable.setValueAt(seatResArr.get(i).getLastName(), i, lastNameCol);
            seatStatusTable.setValueAt(seatResArr.get(i).getAmountPaid(), i, paidCol);
        }
    }
}

/* Makes seats empty */
public static void seatsMakeEmpty(ArrayList<SeatInfo> seatsRes) {
    int i;      // Loop index

    for (i = 0; i < seatsRes.size(); ++i) {
        seatsRes.get(i).makeEmpty();
    }
}

/* Adds empty seats to ArrayList */
public static void seatsAddElements(ArrayList<SeatInfo> seatsRes, int numSeats) {
    int i;     // Loop index

    for (i = 0; i < numSeats; ++i) {
        seatsRes.add(new SeatInfo());
    }
}

/* Creates a SeatReservationFrame and makes it visible */
public static void main(String[] args) {
    // Creates SeatReservationFrame and its components
    SeatReservationFrame myFrame = new SeatReservationFrame();

    myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    myFrame.pack();
    myFrame.setVisible(true);
}
}
```
