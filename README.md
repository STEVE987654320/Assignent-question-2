#include <stdio.h>

// Define the structure for a bank account
typedef struct {
    int account_number;
    float balance;
} Account;

// Function to display the main menu
void display_menu() {
    printf("\nBanking System Menu\n");
    printf("1. Deposit\n");
    printf("2. Withdraw\n");
    printf("3. Check Balance\n");
    printf("4. Exit\n");
}

// Function to display the account selection menu
void display_account_menu() {
    printf("\nSelect an account:\n");
    printf("1. Account 1\n");
    printf("2. Account 2\n");
    printf("3. Account 3\n");
}

int main() {
    // Initialize three bank accounts
    Account accounts[3] = {
        {1, 1000.0},
        {2, 2000.0},
        {3, 3000.0}
    };

    int choice, account_choice;
    float amount;

    while (1) {
        display_menu();
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if (choice == 4) {
            printf("Thank you for using our banking system!\n");
            break;
        }

        display_account_menu();
        printf("Enter your account choice: ");
        scanf("%d", &account_choice);

        // Validate account choice
        if (account_choice < 1 || account_choice > 3) {
            printf("Invalid account choice. Please try again.\n");
            continue;
        }

        switch (choice) {
            case 1:
                printf("Enter the amount to deposit: ");
                scanf("%f", &amount);
                accounts[account_choice - 1].balance += amount;
                printf("Deposit successful. New balance: %.2f\n", accounts[account_choice - 1].balance);
                break;
            case 2:
                printf("Enter the amount to withdraw: ");
                scanf("%f", &amount);
                if (amount > accounts[account_choice - 1].balance) {
                    printf("Insufficient balance. Withdrawal failed.\n");
                } else {
                    accounts[account_choice - 1].balance -= amount;
                    printf("Withdrawal successful. New balance: %.2f\n", accounts[account_choice - 1].balance);
                }
                break;
            case 3:
                printf("Account balance: %.2f\n", accounts[account_choice - 1].balance);
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}

