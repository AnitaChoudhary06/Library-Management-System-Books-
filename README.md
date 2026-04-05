#include <stdio.h>
#include <string.h>

//Struct
struct Book{
    int Book_ID;
    char Book_Name[50];
    char Author_Name[50];
    int Quantity;
};

struct Book B[100];
int count = 0;

//Add Book
void Add_Book(){
    printf("Enter the Book_ID: ");
    scanf("%d", &B[count].Book_ID);
    
    printf("Enter the Book_Name: ");
    scanf("%s", &B[count].Book_Name);
    
    printf("Enter the Author_Name: ");
    scanf("%s", &B[count].Author_Name);
    
    printf("Enter the Quantity of Book: ");
    scanf("%d", B[count].Quantity);
    
    count++;
    printf("Book added successfully. \n");
}

//Display Books
void Display_Books(){
    int i;
    
    if(count == 0){
        printf("No Book are Available. \n");
        return;
    }
    
    printf("\nBook_ID\tBook_Name\tAuthor_Name\tQuantity\n");
    
    for(i = 0; i < count; i++){
        printf("%d\t%s\t%s\t%d\n");
        B[i].Book_ID;
        B[i].Book_Name;
        B[i].Author_Name;
        B[i].Quantity;
    }
}

//Search Book
void Search_Book(){
    int ID, i , found = 0; 
    
    printf("Enter Book_ID for searching: ");
    scanf("%d", &ID);
    
    for(i = 0; i < count; i++){
        if(B[i].Book_ID == ID){
            printf("\nBook Found.\n");
            printf("Book_ID:%d\n Book_Name:%s\n Author_Name: %s\n Quantity: %d\n", 
             B[i].Book_ID,
             B[i].Book_Name,
             B[i].Author_Name,
             B[i].Quantity);
             found = 1;
             break;
        }
    }
    
    if(!found){
        printf("Book Not Found.\n");
    }
}

//Issue Book
void Issue_Book(){
    int ID, i, found = 0;
    
    printf("Enter Book ID to issue: ");
    scanf("%d", &ID);
    
    for(i = 0; i < count; i++){
        if(B[i].Book_ID == ID){
            if(B[i].Quantity > 0){
                B[i].Quantity--;
                printf("Book issued successfully. \n");
            }
            else{
                printf("Book not available. \n");
            }
            found = 1;
            break;
        }
    }
    
    if(!found){
        printf("Book not found. \n");
    }
}

//Return Book
void Return_Book(){
    int ID, i, found = 0;
    
    printf("Enter Book ID to Return: ");
    scanf("%d", &ID);
    
    for(i = 0; i < count; i++){
        if(B[i].Book_ID == ID){
            B[i].Quantity++;
            printf("Book Returned successfully. \n");
            printf("Total Quantity: %d\n", B[i].Quantity);
            found = 1;
            break;
        }
    }
    
    if(!found){
        printf("Book Not Found.\n");
    }
}

//Main Function
int main(){
    int choice;
    
    do{
        printf("\n1. Add_Book\n2. Display_Books\n3. Search_Book\n4.  Issue_Book\n5. Return_Book\n6. Exit\n");
        printf("Enter Choise: ");
        scanf("%d", &choice);
        
        switch(choice){
            case 1: Add_Book(); break;
            case 2: Display_Books(); break;
            case 3: Search_Book(); break;
            case 4: Issue_Book(); break;
            case 5: Return_Book(); break;
            case 6:
            printf("Program exited successfully. \n");
            break;
            
            default:
            printf("Invalid choice. \n ");
        }
    }while(choice != 6);
    
    return 0;
}

