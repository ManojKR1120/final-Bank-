#include<stdio.h>
#include<string.h>
#define max_accounts 150
struct account{
    char name[20];
    int account_number;
};
struct user{
    char username[20];
    int password;
};
struct account account[max_accounts];
int account_count = 0;

int login(struct user);
void create_account();
void transfer_money();
void deduct_money();
void close_account();
void display_account(struct account);

int main()
{
    struct user user = { };
    int choice,login_status;
    login_status=login(user);
    {
        printf("login successfull\n");
    }
    while(1){
        printf("\nBank Management System\n");
        printf("1. Create Account\n");
        printf("2. Transfer Money\n");
        printf("3. Deduct Money\n");
        printf("4. Close Account\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
        case 1:
            create_account();
            break;
        case 2:
            transfer_money();
            break;
        case 3:
            deduct_money();
            break;
        case 4:
            close_account();
            break;
        case 5:
            printf("Exiting the system. Thank you!\n");
            return 0;
        default:
            printf("Invalid choice. Please try again.\n");
        }
    }
    return 0;
}

