import java.applet.Applet;
import java.awt.*;
import java.awt.event.*;

/*
 * <applet code="Q3_SimpleInterestApplet.class" width="400" height="220"></applet>
 */
public class Q3_SimpleInterestApplet extends Applet implements ActionListener {

    private TextField principalField, rateField, monthsField, resultField;
    private Button calculateButton;

    public void init() {
        setLayout(new GridLayout(5, 2, 8, 8));

        add(new Label("Principal Amount (P):"));
        principalField = new TextField();
        add(principalField);

        add(new Label("Annual Rate of Interest (R) %:"));
        rateField = new TextField();
        add(rateField);

        add(new Label("Number of Months (M):"));
        monthsField = new TextField();
        add(monthsField);

        calculateButton = new Button("Calculate Simple Interest");
        calculateButton.addActionListener(this);
        add(calculateButton);

        add(new Label("Simple Interest:"));
        resultField = new TextField();
        resultField.setEditable(false);
        add(resultField);
    }

    public void actionPerformed(ActionEvent e) {
        try {
            double p = Double.parseDouble(principalField.getText().trim());
            double r = Double.parseDouble(rateField.getText().trim());
            double m = Double.parseDouble(monthsField.getText().trim());

            double si = (p * r * m) / (100 * 12);
            resultField.setText(String.format("%.2f", si));
        } catch (NumberFormatException ex) {
            resultField.setText("Enter valid numbers!");
        }
    }

    public static void main(String[] args) {
        Q3_SimpleInterestApplet applet = new Q3_SimpleInterestApplet();
        applet.init();

        Frame frame = new Frame("Simple Interest Calculator");
        frame.add(applet);
        frame.setSize(400, 220);
        frame.addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
        frame.setVisible(true);
    }
}
