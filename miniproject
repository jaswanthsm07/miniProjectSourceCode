#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX 100

struct clientData {
    int acctNum;
    char lastName[20];
    char firstName[20];
    double balance;
};

// function prototypes
void initializeFile();
void createAccount();
void displayAccounts();
void updateAccount();
void deleteAccount();
void checkBalance();
int menu();

int main() {
    char password[20];

 
    printf("Enter password: ");
    scanf("%s", password);

    if (strcmp(password, "admin") != 0) {
        printf("Wrong password! Exiting...\n");
        return 0;
    }

    int choice;
    initializeFile();

    while (1) {
        choice = menu();

        switch (choice) {
            case 1: createAccount(); break;
            case 2: displayAccounts(); break;
            case 3: updateAccount(); break;
            case 4: deleteAccount(); break;
            case 5: checkBalance(); break;
            case 6: 
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice!\n");
        }
    }
}

 
void initializeFile() {
    FILE *fp = fopen("credit.dat", "rb");

    if (fp == NULL) {
        fp = fopen("credit.dat", "wb");

        struct clientData blank = {0, "", "", 0.0};

        for (int i = 0; i < MAX; i++) {
            fwrite(&blank, sizeof(blank), 1, fp);
        }
    }

    fclose(fp);
}

 
int menu() {
    int choice;

    printf("\n===== BANK MENU =====\n");
    printf("1. Create Account\n");
    printf("2. Display Accounts\n");
    printf("3. Update Account\n");
    printf("4. Delete Account\n");
    printf("5. Check Balance\n");
    printf("6. Exit\n");
    printf("Enter choice: ");

    scanf("%d", &choice);
    return choice;
}

 
void createAccount() {
    FILE *fp = fopen("credit.dat", "rb+");
    struct clientData c;
    int acc;

    printf("Enter account number (1-100): ");
    scanf("%d", &acc);

    if (acc < 1 || acc > MAX) {
        printf("Invalid account number!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fread(&c, sizeof(c), 1, fp);

    if (c.acctNum != 0) {
        printf("Account already exists!\n");
        fclose(fp);
        return;
    }

    printf("Enter last name: ");
    scanf("%s", c.lastName);

    printf("Enter first name: ");
    scanf("%s", c.firstName);

    printf("Enter balance: ");
    scanf("%lf", &c.balance);

    c.acctNum = acc;

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fwrite(&c, sizeof(c), 1, fp);

    fclose(fp);

    printf("Account created successfully!\n");
}

 
void displayAccounts() {
    FILE *fp = fopen("credit.dat", "rb");
    struct clientData c;

    printf("\nID   LastName   FirstName   Balance\n");

    while (fread(&c, sizeof(c), 1, fp) == 1) {
        if (c.acctNum != 0) {
            printf("%d   %s   %s   %.2f\n",
                   c.acctNum, c.lastName, c.firstName, c.balance);
        }
    }

    fclose(fp);
}

 
void updateAccount() {
    FILE *fp = fopen("credit.dat", "rb+");
    struct clientData c;
    int acc;
    double amt;

    printf("Enter account number: ");
    scanf("%d", &acc);

    if (acc < 1 || acc > MAX) {
        printf("Invalid account!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fread(&c, sizeof(c), 1, fp);

    if (c.acctNum == 0) {
        printf("Account not found!\n");
        fclose(fp);
        return;
    }

    printf("Current balance: %.2f\n", c.balance);

    printf("Enter amount (+ deposit / - withdraw): ");
    scanf("%lf", &amt);

    if (c.balance + amt < 0) {
        printf("Insufficient balance!\n");
        fclose(fp);
        return;
    }

    c.balance += amt;

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fwrite(&c, sizeof(c), 1, fp);

    fclose(fp);

    printf("Updated successfully!\n");
}

 void deleteAccount() {
    FILE *fp = fopen("credit.dat", "rb+");
    struct clientData c, blank = {0, "", "", 0.0};
    int acc;

    printf("Enter account number: ");
    scanf("%d", &acc);

    if (acc < 1 || acc > MAX) {
        printf("Invalid account!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fread(&c, sizeof(c), 1, fp);

    if (c.acctNum == 0) {
        printf("Account already empty!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fwrite(&blank, sizeof(blank), 1, fp);

    fclose(fp);

    printf("Account deleted!\n");
}

 void checkBalance() {
    FILE *fp = fopen("credit.dat", "rb");
    struct clientData c;
    int acc;

    printf("Enter account number: ");
    scanf("%d", &acc);

    if (acc < 1 || acc > MAX) {
        printf("Invalid account number!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fread(&c, sizeof(c), 1, fp);

    if (c.acctNum == 0) {
        printf("Account not found!\n");
    } else {
        printf("Account Number: %d\n", c.acctNum);
        printf("Name: %s %s\n", c.firstName, c.lastName);
        printf("Balance: %.2f\n", c.balance);
    }

    fclose(fp);
}#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX 100

struct clientData {
    int acctNum;
    char lastName[20];
    char firstName[20];
    double balance;
};
 
void initializeFile();
void createAccount();
void displayAccounts();
void updateAccount();
void deleteAccount();
void checkBalance();
int menu();

int main() {
    char password[20];

     
    printf("Enter password: ");
    scanf("%s", password);

    if (strcmp(password, "admin") != 0) {
        printf("Wrong password! Exiting...\n");
        return 0;
    }

    int choice;
    initializeFile();

    while (1) {
        choice = menu();

        switch (choice) {
            case 1: createAccount(); break;
            case 2: displayAccounts(); break;
            case 3: updateAccount(); break;
            case 4: deleteAccount(); break;
            case 5: checkBalance(); break;
            case 6: 
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice!\n");
        }
    }
}

 
void initializeFile() {
    FILE *fp = fopen("credit.dat", "rb");

    if (fp == NULL) {
        fp = fopen("credit.dat", "wb");

        struct clientData blank = {0, "", "", 0.0};

        for (int i = 0; i < MAX; i++) {
            fwrite(&blank, sizeof(blank), 1, fp);
        }
    }

    fclose(fp);
}

 
int menu() {
    int choice;

    printf("\n===== BANK MENU =====\n");
    printf("1. Create Account\n");
    printf("2. Display Accounts\n");
    printf("3. Update Account\n");
    printf("4. Delete Account\n");
    printf("5. Check Balance\n");
    printf("6. Exit\n");
    printf("Enter choice: ");

    scanf("%d", &choice);
    return choice;
}

 
void createAccount() {
    FILE *fp = fopen("credit.dat", "rb+");
    struct clientData c;
    int acc;

    printf("Enter account number (1-100): ");
    scanf("%d", &acc);

    if (acc < 1 || acc > MAX) {
        printf("Invalid account number!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fread(&c, sizeof(c), 1, fp);

    if (c.acctNum != 0) {
        printf("Account already exists!\n");
        fclose(fp);
        return;
    }

    printf("Enter last name: ");
    scanf("%s", c.lastName);

    printf("Enter first name: ");
    scanf("%s", c.firstName);

    printf("Enter balance: ");
    scanf("%lf", &c.balance);

    c.acctNum = acc;

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fwrite(&c, sizeof(c), 1, fp);

    fclose(fp);

    printf("Account created successfully!\n");
}

 
void displayAccounts() {
    FILE *fp = fopen("credit.dat", "rb");
    struct clientData c;

    printf("\nID   LastName   FirstName   Balance\n");

    while (fread(&c, sizeof(c), 1, fp) == 1) {
        if (c.acctNum != 0) {
            printf("%d   %s   %s   %.2f\n",
                   c.acctNum, c.lastName, c.firstName, c.balance);
        }
    }

    fclose(fp);
}

 
void updateAccount() {
    FILE *fp = fopen("credit.dat", "rb+");
    struct clientData c;
    int acc;
    double amt;

    printf("Enter account number: ");
    scanf("%d", &acc);

    if (acc < 1 || acc > MAX) {
        printf("Invalid account!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fread(&c, sizeof(c), 1, fp);

    if (c.acctNum == 0) {
        printf("Account not found!\n");
        fclose(fp);
        return;
    }

    printf("Current balance: %.2f\n", c.balance);

    printf("Enter amount (+ deposit / - withdraw): ");
    scanf("%lf", &amt);

    if (c.balance + amt < 0) {
        printf("Insufficient balance!\n");
        fclose(fp);
        return;
    }

    c.balance += amt;

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fwrite(&c, sizeof(c), 1, fp);

    fclose(fp);

    printf("Updated successfully!\n");
}

 
void deleteAccount() {
    FILE *fp = fopen("credit.dat", "rb+");
    struct clientData c, blank = {0, "", "", 0.0};
    int acc;

    printf("Enter account number: ");
    scanf("%d", &acc);

    if (acc < 1 || acc > MAX) {
        printf("Invalid account!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fread(&c, sizeof(c), 1, fp);

    if (c.acctNum == 0) {
        printf("Account already empty!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fwrite(&blank, sizeof(blank), 1, fp);

    fclose(fp);

    printf("Account deleted!\n");
}

 
void checkBalance() {
    FILE *fp = fopen("credit.dat", "rb");
    struct clientData c;
    int acc;

    printf("Enter account number: ");
    scanf("%d", &acc);

    if (acc < 1 || acc > MAX) {
        printf("Invalid account number!\n");
        fclose(fp);
        return;
    }

    fseek(fp, (acc - 1) * sizeof(c), SEEK_SET);
    fread(&c, sizeof(c), 1, fp);

    if (c.acctNum == 0) {
        printf("Account not found!\n");
    } else {
        printf("Account Number: %d\n", c.acctNum);
        printf("Name: %s %s\n", c.firstName, c.lastName);
        printf("Balance: %.2f\n", c.balance);
    }

    fclose(fp);
}
