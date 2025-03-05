import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

class BankAccount {
    private String accountHolder;
    private double balance;

    // Constructor to initialize a new account
    public BankAccount(String accountHolder, double initialDeposit) {
        this.accountHolder = accountHolder;
        this.balance = initialDeposit;
    }

    // Deposit money into the account
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: " + amount);
        } else {
            System.out.println("Deposit amount must be positive.");
        }
    }

    // Withdraw money from the account
    public void withdraw(double amount) {
        if (amount <= balance && amount > 0) {
            balance -= amount;
            System.out.println("Withdrew: " + amount);
        } else if (amount <= 0) {
            System.out.println("Withdrawal amount must be positive.");
        } else {
            System.out.println("Insufficient balance.");
        }
    }

    // Display account balance
    public void displayBalance() {
        System.out.println("Account Holder: " + accountHolder);
        System.out.println("Current Balance: " + balance);
    }

    // Get the account holder's name
    public String getAccountHolder() {
        return accountHolder;
    }
}

class Bank {
    private Map<Integer, BankAccount> accounts; // Storing accounts by account ID
    private int accountIdCounter;

    // Constructor to initialize the Bank system
    public Bank() {
        accounts = new HashMap<>();
        accountIdCounter = 1; // Start account IDs from 1
    }

    // Create a new account
    public int createAccount(String accountHolder, double initialDeposit) {
        BankAccount newAccount = new BankAccount(accountHolder, initialDeposit);
        accounts.put(accountIdCounter, newAccount);
        System.out.println("Account created for " + accountHolder + " with initial deposit of " + initialDeposit);
        return accountIdCounter++; // Return the newly created account ID and increment the counter
    }

    // Delete an account
    public void deleteAccount(int accountId) {
        if (accounts.containsKey(accountId)) {
            accounts.remove(accountId);
            System.out.println("Account ID " + accountId + " has been deleted.");
        } else {
            System.out.println("Account ID " + accountId + " does not exist.");
        }
    }

    // Get the BankAccount object by account ID
    public BankAccount getAccount(int accountId) {
        return accounts.get(accountId);
    }
}

public class SimpleBankingSystem {
    public static void main(String[] args) {
        Bank bank = new Bank();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\n--- Banking Management System ---");
            System.out.println("1. Create Account");
            System.out.println("2. Delete Account");
            System.out.println("3. Deposit");
            System.out.println("4. Withdraw");
            System.out.println("5. Display Balance");
            System.out.println("6. Exit");
            System.out.print("Choose an option: ");
            int option = scanner.nextInt();

            int accountId;
            BankAccount account;

            switch (option) {
                case 1:
                    System.out.print("Enter account holder name: ");
                    scanner.nextLine();  // Consume newline
                    String accountHolder = scanner.nextLine();
                    System.out.print("Enter initial deposit: ");
                    double initialDeposit = scanner.nextDouble();
                    accountId = bank.createAccount(accountHolder, initialDeposit);
                    break;

                case 2:
                    System.out.print("Enter account ID to delete: ");
                    accountId = scanner.nextInt();
                    bank.deleteAccount(accountId);
                    break;

                case 3:
                    System.out.print("Enter account ID to deposit into: ");
                    accountId = scanner.nextInt();
                    account = bank.getAccount(accountId);
                    if (account != null) {
                        System.out.print("Enter amount to deposit: ");
                        double depositAmount = scanner.nextDouble();
                        account.deposit(depositAmount);
                    } else {
                        System.out.println("Account not found.");
                    }
                    break;

                case 4:
                    System.out.print("Enter account ID to withdraw from: ");
                    accountId = scanner.nextInt();
                    account = bank.getAccount(accountId);
                    if (account != null) {
                        System.out.print("Enter amount to withdraw: ");
                        double withdrawAmount = scanner.nextDouble();
                        account.withdraw(withdrawAmount);
                    } else {
                        System.out.println("Account not found.");
                    }
                    break;

                case 5:
                    System.out.print("Enter account ID to display balance: ");
                    accountId = scanner.nextInt();
                    account = bank.getAccount(accountId);
                    if (account != null) {
                        account.displayBalance();
                    } else {
                        System.out.println("Account not found.");
                    }
                    break;

                case 6:
                    System.out.println("Exiting system...");
                    scanner.close();
                    return;

                default:
                    System.out.println("Invalid option, please try again.");
            }
        }
    }
}
