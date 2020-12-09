# Singly Linked List

### Q. Write a menu driven program in C to implement a singly linked list and to perform the following: Insert a node at the beginning of the list, insert a node after a particular node in the list, insert a node at the end of the list, delete a node containing a particular item.
```
#include <stdio.h>
#include <stdlib.h>

struct node
{
    int data;
    struct node *link;
} *head = NULL, *tail = NULL;

void insertAtBeg()
{
    int x;
    printf("Enter data to insert: ");
    scanf("%d", &x);
    if (head == NULL)
    {
        head = (struct node *)malloc(sizeof(struct node));
        head->data = x;
        head->link = NULL;
    }
    else
    {
        struct node *temp = (struct node *)malloc(sizeof(struct node));
        temp->data = x;
        temp->link = head;
        head = temp;
    }
}

void insertAtPos()
{
    int x, i = 0, n;
    struct node *temp = head;
    printf("Enter position to insert after: ");
    scanf("%d", &n);
    printf("Enter data to insert: ");
    scanf("%d", &x);

    while (temp != NULL && i < n)
    {
        temp = temp->link;
        i++;
    }
    if (temp == NULL)
    {
        printf("Error.\n");
        return;
    }
    struct node *temp2 = (struct node *)malloc(sizeof(struct node));
    temp2->data = x;
    temp2->link = temp->link;
    temp->link = temp2;
}

void insertAtEnd()
{
    int x;
    printf("Enter data to insert: ");
    scanf("%d", &x);
    if (head == NULL)
    {
        head = (struct node *)malloc(sizeof(struct node));
        head->data = x;
        head->link = NULL;
    }
    else
    {
        struct node *temp = head;
        while (temp->link != NULL)
        {
            temp = temp->link;
        }
        struct node *temp2 = (struct node *)malloc(sizeof(struct node));
        temp2->data = x;
        temp2->link = NULL;
        temp->link = temp2;
    }
}

void deleteNode()
{
    int x, flag = 0;
    printf("Enter data to delete: ");
    scanf("%d", &x);
    struct node *temp = head, *prev;
    if (temp != NULL && temp->data == x)
    {
        head = temp->link;
        free(temp);
        return;
    }
    while (temp != NULL && temp->data != x)
    {
        prev = temp;
        temp = temp->link;
    }
    if (temp == NULL)
    {
        printf("Element not found.\n");
        return;
    }
    prev->link = temp->link;
    free(temp);
}

void display()
{
    struct node *temp = head;
    printf("The list is as follows:\n");
    while (temp != NULL)
    {
        printf("%d ", temp->data);
        temp = temp->link;
    }
}

int main(void) 
{
  int ch = 0;
    do
    {
      printf("\n1) Insert a node at the beginning of the list\n2) Insert a node after a particular node in the list\n3) Insert a node at the end of the list\n4) Delete a node containing a particular item\n5) Display linked list\n6) Exit\nEnter your choice: ");
      scanf("%d", &ch);
      switch (ch)
      {
      case 1: insertAtBeg(); break;
      case 2: insertAtPos(); break;
      case 3: insertAtEnd(); break;
      case 4: deleteNode(); break;
      case 5: display(); break;
      }
    }while (ch < 6);

    return 0;
}
```