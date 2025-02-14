int login(struct user user){
    char username[20];
    int password[20];
    printf("enter the username\n");
    scanf("%s",&username);
    printf("enter the password\n");
    scanf("%d",&password);
    if (username&&password){
        printf("login sucessfull");
    } else {
        printf("login failed");
    }
}
void create_account(){
    struct account new_account;
    char name[20];
    int account_number;
    float balance = 0.0;
    printf("enter the name\n");
    scanf("%s",&new_account);
    printf("enter the account number\n");
    scanf("%d",&new_account.account_number);
    //  fgets(new_account.name, sizeof(new_account.name), stdin);
    new_account.name[strcspn(new_account.name, "\n")] = '\0';
    account[account_count++] = new_account;
    printf("Account created successfully.\n");
}
void check_balance(){
    int account_number, found = 0;
    printf("Enter Account Number to check balance: ");
    scanf("%d", &account_number);
    for (int i = 0; i < account_count; i++) {
        if (account[i].account_number == account_number) {
            display_account(account[i]);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("Account not found.\n");
    }
}
void transfer_money(){
    int from_account, to_account;
    float amount;
    int found_from = 0;
    int found_to = 0;
    printf("Enter Source Account Number: ");
    scanf("%d", &from_account);
    printf("Enter Destination Account Number: ");
    scanf("%d", &to_account);
    printf("Enter amount to transfer: ");
    scanf("%f", &amount);
    for (int i = 0; i < account_count; i++) {
        if (account[i].account_number == from_account) {
            found_from = 1;
            break;
        } 
        else {
            printf("Insufficient balance in source account.\n");
            return;
        }
    }
    if (found_from && found_to) {
        printf("Transfer successful.\n");
    } else {
        printf("Invalid account details. Transfer failed.\n");
    }
}
void deduct_money(){
    int account_number;
    float amount;
    int found = 0;
    printf("Enter Account Number: ");
    scanf("%d", &account_number);
    printf("Enter amount to deduct: ");
    scanf("%f", &amount);
    for (int i = 0; i < account_count; i++) {
        if (account[i].account_number == account_number) {
            found = 1;
            printf("Money deducted successfully. Current balance: %.2f\n");
        } else {
            printf("Insufficient balance.\n");
        }
        break;
    }
    if (!found) {
        printf("Account not found.\n");
    }
}
void close_account(){
    int account_number, found = 0;
    printf("Enter Account Number to close: ");
    scanf("%d", &account_number);
    for (int i = 0; i < account_count; i++) {
        if (account[i].account_number == account_number) {
            account_count--;
            found = 1;
            printf("Account closed successfully.\n");
            break;
        }
    }
    if (!found) {
        printf("Account not found.\n");
    }
}
void display_account(struct account account) {
    printf("\nAccount Number: %d\n", account.account_number);
    printf("Account Holder Name: %s\n", account.name);
}
