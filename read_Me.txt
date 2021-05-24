package com.loan;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionListener;
import java.text.*;
import java.awt.event.ActionEvent;
import javax.swing.border.LineBorder;
import java.awt.Window.Type;

public class LoanAssistant {

	private JFrame FrameLoan;
	private JTextField balanceTextField;
	private JTextField interestTextField;
	private JTextField paymentTextField;
	private JTextField monthsTextField;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					LoanAssistant window = new LoanAssistant();
					window.FrameLoan.setVisible(true);
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the application.
	 */
	public LoanAssistant() {
		initialize();
	}

	/**
	 * Initialize the contents of the frame.
	 */
	private void initialize() {
		// Creating the Frame
		
		//Frame outer structure and inner Layout
		FrameLoan = new JFrame();
		FrameLoan.setVisible(true);
		FrameLoan.setSize(new Dimension(5, 5));
		FrameLoan.setPreferredSize(new Dimension(5, 5));
		FrameLoan.setForeground(Color.BLACK);
		FrameLoan.setFont(new Font("Algerian", Font.BOLD, 20));
		FrameLoan.setBackground(Color.BLACK);
		FrameLoan.setTitle("Loan Assistant");
		FrameLoan.setBounds(100, 100, 892, 546);
		FrameLoan.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		GridBagLayout gridBagLayout = new GridBagLayout();
		gridBagLayout.columnWidths = new int[] {0, 0, 0, 10, 0};
		gridBagLayout.rowHeights = new int[]{0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0};
		gridBagLayout.columnWeights = new double[]{0.0, 0.0, 0.0, 0.0, 1.0};
		gridBagLayout.rowWeights = new double[]{0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, Double.MIN_VALUE};
		FrameLoan.getContentPane().setLayout(gridBagLayout);
		
		//creating Loan Balance label
		
		JLabel loanBalanceLabel = new JLabel("Loan Balance");
		loanBalanceLabel.setFont(new Font("Times New Roman", Font.BOLD, 20));
		GridBagConstraints gbc_loanBalanceLabel = new GridBagConstraints();
		gbc_loanBalanceLabel.fill = GridBagConstraints.BOTH;
		gbc_loanBalanceLabel.insets = new Insets(10, 10, 5, 5);	
		gbc_loanBalanceLabel.gridx = 1;
		gbc_loanBalanceLabel.gridy = 1;
		FrameLoan.getContentPane().add(loanBalanceLabel, gbc_loanBalanceLabel);
		
		//creating Load Balance text Field for taking loan balance input from user.
		
		balanceTextField = new JTextField();
		GridBagConstraints gbc_balanceTextField = new GridBagConstraints();
		gbc_balanceTextField.anchor = GridBagConstraints.WEST;
		gbc_balanceTextField.insets = new Insets(10, 10, 5, 10);
		gbc_balanceTextField.gridx = 2;
		gbc_balanceTextField.gridy = 1;
		FrameLoan.getContentPane().add(balanceTextField, gbc_balanceTextField);
		balanceTextField.setColumns(10);
		//declaring a method to receive action events from this text field and implement it.
		
		balanceTextField.addActionListener(new ActionListener()
				{
					public void actionPerformed(ActionEvent e) {
						balanceTextFieldActionPerformed(e);
					}
				});
		
		//creating Loan Analysis label
		
		loanAnalysis = new JLabel("Loan Analysis:");
		loanAnalysis.setFont(new Font("Rockwell", Font.BOLD, 18));
		GridBagConstraints gbc_loanAnalysis = new GridBagConstraints();
		gbc_loanAnalysis.anchor = GridBagConstraints.WEST;
		gbc_loanAnalysis.insets = new Insets(0, 0, 5, 0);
		gbc_loanAnalysis.gridx = 4;
		gbc_loanAnalysis.gridy = 1;
		FrameLoan.getContentPane().add(loanAnalysis, gbc_loanAnalysis);
		
		//creating Loan Analysis text Area to show the output of the analysis.
		
		analysisTextArea = new JTextArea();
		analysisTextArea.setFocusable(false);
		analysisTextArea.setEditable(false);
		analysisTextArea.setBackground(new Color(255, 255, 255));
		analysisTextArea.setBorder(new LineBorder(new Color(0, 0, 0), 3));
		GridBagConstraints gbc_analysisTextArea = new GridBagConstraints();
		gbc_analysisTextArea.gridheight = 8;
		gbc_analysisTextArea.insets = new Insets(20, 20, 20, 20);
		gbc_analysisTextArea.fill = GridBagConstraints.BOTH;
		gbc_analysisTextArea.gridx = 4;
		gbc_analysisTextArea.gridy = 2;
		FrameLoan.getContentPane().add(analysisTextArea, gbc_analysisTextArea);
		
		//creating Interest Rate label
		
		JLabel interestLabel = new JLabel("Interest Rate");
		interestLabel.setFont(new Font("Times New Roman", Font.BOLD, 20));
		GridBagConstraints gbc_interestLabel = new GridBagConstraints();
		gbc_interestLabel.anchor = GridBagConstraints.WEST;
		gbc_interestLabel.insets = new Insets(10, 10, 5, 5);
		gbc_interestLabel.gridx = 1;
		gbc_interestLabel.gridy = 3;
		FrameLoan.getContentPane().add(interestLabel, gbc_interestLabel);
		
		//creating interest text field to take interest rate input from user
		
		interestTextField = new JTextField();
		GridBagConstraints gbc_interestTextField = new GridBagConstraints();
		gbc_interestTextField.insets = new Insets(10, 10, 5, 10);
		gbc_interestTextField.anchor = GridBagConstraints.WEST;
		gbc_interestTextField.gridx = 2;
		gbc_interestTextField.gridy = 3;
		FrameLoan.getContentPane().add(interestTextField, gbc_interestTextField);
		interestTextField.setColumns(10);
		interestTextField.addActionListener(new ActionListener ()
				//declaring a method to receive action events from this text field and implement it.
		{
			public void actionPerformed(ActionEvent e)
				{
					interestTextFieldActionPerformed(e);
				}
		});
		
		/*creating the radio button to select  no. of payment.
			And to compute monthly payment.
		*/
		paymentRadioButton = new JRadioButton("");
		GridBagConstraints gbc_paymentRadioButton = new GridBagConstraints();
		gbc_paymentRadioButton.anchor = GridBagConstraints.SOUTH;
		gbc_paymentRadioButton.insets = new Insets(0, 0, 5, 5);
		gbc_paymentRadioButton.gridx = 0;
		gbc_paymentRadioButton.gridy = 5;
		FrameLoan.getContentPane().add(paymentRadioButton, gbc_paymentRadioButton);
		paymentRadioButton.setFocusable(false);
		paymentRadioButton.setToolTipText("press it if you have no. of payments.");
		
		//declaring a method to receive action events for this radio button.
		paymentRadioButton.addActionListener(new ActionListener()
		{
			public void actionPerformed(ActionEvent e)
				{
					buttonActionPerformed(e); //call a method body buttonActionPerformed.
				}
		});

		//creating a label of number of payments
		JLabel paymentLabel = new JLabel("Number Of Payments");
		paymentLabel.setFont(new Font("Times New Roman", Font.BOLD, 20));
		GridBagConstraints gbc_paymentLabel = new GridBagConstraints();
		gbc_paymentLabel.anchor = GridBagConstraints.EAST;
		gbc_paymentLabel.insets = new Insets(10, 10, 5, 5);
		gbc_paymentLabel.gridx = 1;
		gbc_paymentLabel.gridy = 5;
		FrameLoan.getContentPane().add(paymentLabel, gbc_paymentLabel);
		
		//creating the number of payments text field area for taking input from user.
		
		paymentTextField = new JTextField();
		GridBagConstraints gbc_paymentTextField = new GridBagConstraints();
		gbc_paymentTextField.insets = new Insets(10, 10, 5, 10);
		gbc_paymentTextField.anchor = GridBagConstraints.WEST;
		gbc_paymentTextField.gridx = 2;
		gbc_paymentTextField.gridy = 5;
		FrameLoan.getContentPane().add(paymentTextField, gbc_paymentTextField);
		paymentTextField.setColumns(10);
		paymentTextField.addActionListener(new ActionListener ()
		{
		public void actionPerformed(ActionEvent e)
		{
			paymentTextFieldActionPerformed(e);
		}
		});
		/*creating the radio button to select  monthly payment.
			And to compute no. of payments.
		 */
        monthsRadioButton = new JRadioButton("");
        monthsRadioButton.setFocusable(false);
        GridBagConstraints gbc_monthsRadioButton = new GridBagConstraints();
        gbc_monthsRadioButton.anchor = GridBagConstraints.SOUTH;
        gbc_monthsRadioButton.insets = new Insets(0, 0, 5, 5);
        gbc_monthsRadioButton.gridx = 0;
        gbc_monthsRadioButton.gridy = 7;
        FrameLoan.getContentPane().add(monthsRadioButton, gbc_monthsRadioButton);
		monthsRadioButton.setToolTipText("press to compute numbers of payment.");
		
		//declaring the method to receive action for a method call and to perform the actions on this radio button.
		monthsRadioButton.addActionListener(new ActionListener()
			{
				public void actionPerformed(ActionEvent e)
					{
						monthsActionPerformed(e);	//method call
					}
			});
		
        //creating the monthly payment label 
		
		JLabel monthlyLabel = new JLabel("Monthly Payment");
		monthlyLabel.setFont(new Font("Times New Roman", Font.BOLD, 20));
		GridBagConstraints gbc_monthlyLabel = new GridBagConstraints();
		gbc_monthlyLabel.anchor = GridBagConstraints.WEST;
		gbc_monthlyLabel.insets = new Insets(10, 10, 5, 5);
		gbc_monthlyLabel.gridx = 1;
		gbc_monthlyLabel.gridy = 7;
		FrameLoan.getContentPane().add(monthlyLabel, gbc_monthlyLabel);
		
		//creating the monthly payment text field to receive the input from user
		
		monthsTextField = new JTextField();
		GridBagConstraints gbc_monthsTextField = new GridBagConstraints();
		gbc_monthsTextField.insets = new Insets(10, 10, 5, 10);
		gbc_monthsTextField.anchor = GridBagConstraints.WEST;
		gbc_monthsTextField.gridx = 2;
		gbc_monthsTextField.gridy = 7;
		FrameLoan.getContentPane().add(monthsTextField, gbc_monthsTextField);
		monthsTextField.setColumns(10);
		
		//declaring a method to receive actions from the method call and to implement in this field area.
		
		monthsTextField.addActionListener(new ActionListener ()
			{
				public void actionPerformed(ActionEvent e)
					{
						monthsTextFieldActionPerformed(e);	//method call
					}
			});
		
		/*creating the compute button for user to click it to compute
			monthly payment or number of payments.*/
		
		computeButton = new JButton("Compute Monthly Payment");
		computeButton.setFont(new Font("Rockwell", Font.BOLD, 16));
		GridBagConstraints gbc_computeButton = new GridBagConstraints();
		gbc_computeButton.fill = GridBagConstraints.HORIZONTAL;
		gbc_computeButton.gridwidth = 2;
		gbc_computeButton.insets = new Insets(10, 10, 5, 5);
		gbc_computeButton.gridx = 1;
		gbc_computeButton.gridy = 9;
		FrameLoan.getContentPane().add(computeButton, gbc_computeButton);
		
		//declaring compute method to receive action from a call method and to implement it on compute button.
		computeButton.addActionListener(new ActionListener()
			{
				public void actionPerformed(ActionEvent e)
					{
						computeButtonActionPerformed(e);	//method call
					}
			});
		
		//creating the new loan analysis button to perform new loan analysis
		newLoanButton = new JButton("New Loan Analysis");
		newLoanButton.setFont(new Font("Rockwell", Font.BOLD, 16));
		GridBagConstraints gbc_newLoanButton = new GridBagConstraints();
		gbc_newLoanButton.fill = GridBagConstraints.HORIZONTAL;
		gbc_newLoanButton.gridwidth = 2;
		gbc_newLoanButton.insets = new Insets(10, 10, 5, 5);
		gbc_newLoanButton.gridx = 1;
		gbc_newLoanButton.gridy = 10;
		FrameLoan.getContentPane().add(newLoanButton, gbc_newLoanButton);
		
		//declaring new loan method to receive action from a call method and to implement it on this button.
		newLoanButton.addActionListener(new ActionListener()
			{
				public void actionPerformed(ActionEvent e)
					{
						newLoanButtonActionPerformed(e);
					}
			});
		
		//creating the exit button to exit or the application
		exitButton = new JButton("Exit");
		exitButton.setFont(new Font("Rockwell", Font.BOLD, 20));
		GridBagConstraints gbc_exitButton = new GridBagConstraints();
		gbc_exitButton.insets = new Insets(0, 0, 5, 0);
		gbc_exitButton.gridx = 4;
		gbc_exitButton.gridy = 10;
		FrameLoan.getContentPane().add(exitButton, gbc_exitButton);
		
		//declaring a method to receive action from method call and to implement it on this button
		exitButton.addActionListener(new ActionListener()
		{	public void actionPerformed(ActionEvent e)
				{
					exitButtonActionPerformed(e);
				}
		});
	}
	
	/**
	 * Declaring the content of frame
	 */
	Color lightYellow = new Color(255, 255, 128);
	boolean computePayment;
	private JTextArea analysisTextArea;
	private JLabel loanAnalysis;
	private JButton computeButton;
	private JButton newLoanButton;
	private JButton exitButton;
	private JRadioButton paymentRadioButton;
	private JRadioButton monthsRadioButton;
	
	/**
	 * defining all the action method perform on the content of frame
	 * @param e
	 */
	
	private void buttonActionPerformed(ActionEvent e)
		{	
			computePayment = false;
			paymentRadioButton.setVisible(true);
			monthsRadioButton.setVisible(false);
			monthsTextField.setText("");
			monthsTextField.setEditable(false);
			monthsTextField.setFocusable(false);
			monthsTextField.setBackground(lightYellow);
			paymentTextField.setEditable(true);
			paymentTextField.setBackground(Color.WHITE);
			paymentTextField.setFocusable(true);
			computeButton.setText("Compute monthly payment");
			balanceTextField.requestFocus();
		}
		
	
	private void monthsActionPerformed(ActionEvent e)
		{	// will compute number of payments
			computePayment = true;
			paymentRadioButton.setVisible(false);
			monthsRadioButton.setVisible(true);
			monthsTextField.setEditable(true);
			monthsTextField.setFocusable(true);
			monthsTextField.setBackground(Color.WHITE);
			paymentTextField.setText("");
			paymentTextField.setEditable(false);
			paymentTextField.setBackground(lightYellow);
			paymentTextField.setFocusable(false);
			computeButton.setText("Compute number of payment");
			balanceTextField.requestFocus();
		}
	
	private void newLoanButtonActionPerformed(ActionEvent e)
		{
			// clear computed value and analysis
			if (computePayment)
				{
					monthsTextField.setText("");
					paymentRadioButton.setEnabled(true);
					paymentRadioButton.setVisible(true);
				}
			else
				{
					paymentTextField.setText("");
					monthsRadioButton.setEnabled(true);
					monthsRadioButton.setVisible(true);
		}
		analysisTextArea.setText("");
		computeButton.setEnabled(true);
		newLoanButton.setEnabled(true);
		balanceTextField.requestFocus();
		}
	
	private void computeButtonActionPerformed(ActionEvent e)
		{	//declaring variables.
			double balance, interest, payment;
			int months;
			double monthlyInterest, multiplier;
			double loanBalance, finalPayment;
			
		//condition to check whether the Loan balance input is valid input or not
			if(validateDecimalNumber(balanceTextField)) {
				balance = 
						Double.valueOf(balanceTextField.getText()).doubleValue();
			}
			else
				{
					JOptionPane.showConfirmDialog(null, "Invalid or empty Loan Balance entry.\nPlease correct.", "Balance Input Error", JOptionPane.DEFAULT_OPTION,JOptionPane.INFORMATION_MESSAGE);
					return ;
				}
		//condition to check whether the Interest Rate input is valid or not.	
			if(validateDecimalNumber(interestTextField)) {
					interest = Double.valueOf(interestTextField.getText()).doubleValue();
				}
			else {
					JOptionPane.showConfirmDialog(null, "Invalid or empty Interest Rate entry.\nPlease correct.", "Interest Input Error", JOptionPane.DEFAULT_OPTION,JOptionPane.INFORMATION_MESSAGE);
					return;
				}
		//calculating monthly interest
		monthlyInterest = interest / 1200;
		
		//condition for checking whether to use first method of computing monthly payment or second method computing no. of payments 
		if(computePayment==false) {
		// Compute loan payment
			//condition to check whether the numbers of payments input is valid/empty or not	
				if(validateDecimalNumber(paymentTextField)) {
						months = Integer.valueOf(paymentTextField.getText()).intValue();
					}
				else {
						JOptionPane.showConfirmDialog(null, "Invalid or empty Number of Payments entry.\nPlease correct.", "Number of Payments Input Error",JOptionPane.DEFAULT_OPTION, JOptionPane.INFORMATION_MESSAGE);
						return;
					}
				//calculating monthly payment when interest rate is zero.
				if (interest == 0)
					{
						payment = balance / months;
					}
				else
					{
						multiplier = Math.pow(1 + monthlyInterest, months);
						payment = balance * monthlyInterest * multiplier / (multiplier - 1);
					}
				monthsTextField.setText(new DecimalFormat("0.00").format(payment));
			}
		else {	
		// Compute number of payments
			//checking condition whether the input monthly payment is valid/empty or not
			if(validateDecimalNumber(monthsTextField)) {
						payment =
						Double.valueOf(monthsTextField.getText()).doubleValue();
					
					//checking whether the input monthly payment is below minimum payment or not.	
					if (payment <= (balance * monthlyInterest + 1.0))
						{
					 		if (JOptionPane.showConfirmDialog(null, "Minimum payment must be $" +
					 				new DecimalFormat("0.00").format((int)(balance * monthlyInterest + 1.0)) + "\n" + "Do youwant to use the minimum payment?", "Input Error", JOptionPane.YES_NO_OPTION,JOptionPane.QUESTION_MESSAGE) == JOptionPane.YES_OPTION)
					 		{
					 				paymentTextField.setText(new DecimalFormat("0.00").format((int)(balance * monthlyInterest + 1.0)));
					 				payment = Double.valueOf(paymentTextField.getText()).doubleValue();
					 		}
					 		else
					 		{
					 			paymentTextField.requestFocus();
					 			return;
					 		}
						}	
			}
			else {
					JOptionPane.showConfirmDialog(null, "Invalid or empty Monthly Payment entry.\nPlease correct.", "Payment Input Error", JOptionPane.DEFAULT_OPTION,JOptionPane.INFORMATION_MESSAGE);
					return;
				}
			
			if (interest == 0)
				{
					months = (int)(balance / payment);
				}
			else
				{
					months = (int)((Math.log(payment) - Math.log(payment - balance *monthlyInterest)) / Math.log(1 + monthlyInterest));
				}

			paymentTextField.setText(String.valueOf(months));
			
		
		}
	
	
		// reset payment prior to analysis to fix at two decimals
		payment = Double.valueOf(monthsTextField.getText()).doubleValue();
		
		// show analysis
		analysisTextArea.setText("Loan Balance: $" + new DecimalFormat("0.00").format(balance));
		analysisTextArea.append("\n" + "Interest Rate: " + new DecimalFormat("0.00").format(interest) + "%");
		
		// process all but last payment
		loanBalance = balance;
		for (int paymentNumber = 1; paymentNumber <= months - 1; paymentNumber++)
				{
					loanBalance += loanBalance * monthlyInterest - payment;
				}
		// find final payment
		finalPayment = loanBalance;
			if (finalPayment > payment)
				{
					// apply one more payment
					loanBalance += loanBalance * monthlyInterest - payment;
					finalPayment = loanBalance;
					months++;
					paymentTextField.setText(String.valueOf(months));
				}
			
		// showing the loan analysis in loan analysis text field area	
		analysisTextArea.append("\n\n" + String.valueOf(months - 1) + " Payments of $" + new DecimalFormat("0.00").format(payment));
		analysisTextArea.append("\n" + "Final Payment of: $" + new DecimalFormat("0.00").format(finalPayment));
		analysisTextArea.append("\n" + "Total Payments: $" + new DecimalFormat("0.00").format((months - 1) * payment + finalPayment));
		analysisTextArea.append("\n" + "Interest Paid $" + new DecimalFormat("0.00").format((months - 1) * payment + finalPayment - balance));
		
		computeButton.setEnabled(false);
		newLoanButton.setEnabled(true);
		newLoanButton.requestFocus();
	}
	
	private void exitButtonActionPerformed(ActionEvent e)
		{
			System.exit(0);
		}
	private void balanceTextFieldActionPerformed(ActionEvent e) {
			balanceTextField.transferFocus();
		}
	private void interestTextFieldActionPerformed(ActionEvent e) {
			interestTextField.transferFocus();
		}
	private void paymentTextFieldActionPerformed(ActionEvent e) {
			paymentTextField.transferFocus();
		}
	private void monthsTextFieldActionPerformed(ActionEvent e) {
			monthsTextField.transferFocus();
		}
	public boolean validateDecimalNumber(JTextField tf)
		{
		// checks to see if text field contains
		// valid decimal number with only digits and a single decimal point
			String s = tf.getText().trim();
			boolean hasDecimal = false;
			boolean valid = true;
			if (s.length() == 0)
				{
					valid = false;
				}
			else
				{
					for (int i = 0; i < s.length(); i++)
					{
						char c = s.charAt(i);
						if (c >= '0' && c <= '9')
							{
								continue;
							}
						else if (c == '.' && !hasDecimal)
							{
								hasDecimal = true;
							}
						else
							{
								// invalid character found
								valid = false;
								}
					}
				}
		tf.setText(s);
		if (!valid)
			{
				tf.requestFocus();
			}
		return (valid);
	}

}
/**
 * END OF APLLICATION PROGRAM
*/