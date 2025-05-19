# Codinimport java.util.Scanner;

public class ATM {

    static double balance = 1000;
    static String correctUserId = "1234";
    static String correctPin = "0000";

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.println("Welcome to the ATM!");

        boolean isLoggedIn = false;
        int attempts = 3;

        while (attempts > 0) {
            System.out.print("Enter User ID: ");
            String userId = input.next();

            System.out.print("Enter PIN: ");
            String pin = input.next();

            if (userId.equals(correctUserId) && pin.equals(correctPin)) {
                isLoggedIn = true;
                break;
            } else {
                attempts--;
                System.out.println("Wrong ID or PIN. Attempts left: " + attempts);
            }
        }

        if (!isLoggedIn) {
            System.out.println("Too many failed attempts. Exiting...");
            return;
        }

        int choice;
        do {
            System.out.println("\n--- ATM Menu ---");
            System.out.println("1. Check Balance");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            choice = input.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("Your balance is: $" + balance);
                    break;
                case 2:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = input.nextDouble();
                    if (depositAmount > 0) {
                        balance += depositAmount;
                        System.out.println("Deposited: $" + depositAmount);
                    } else {
                        System.out.println("Invalid amount.");
                    }
                    break;
                case 3:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = input.nextDouble();
                    if (withdrawAmount > 0 && withdrawAmount <= balance) {
                        balance -= withdrawAmount;
                        System.out.println("Withdrawn: $" + withdrawAmount);
                    } else {
                        System.out.println("Not enough
