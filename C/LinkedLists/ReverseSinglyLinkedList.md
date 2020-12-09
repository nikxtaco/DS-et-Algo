# Reverse Singly Linked List

### Q. Reverse a given singly linked list.
```
#include <stdio.h>
#include <stdlib.h>

struct node{
    int data;
    struct node *link;
} *head = NULL;

void insert(int x)
{
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

void reverse()
{
    struct node *now = head, *next = NULL, *prev = NULL;
    while (now != NULL)
    {
        next = now->link;
        now->link = prev;
        prev = now;
        now = next;
    }
    head = prev;
}

void display()
{
    struct node *temp = head;
    while (temp != NULL)
    {
        printf("%d ", temp->data);
        temp = temp->link;
    }
}

int main(void)
{
    int n;
    printf("Enter the number of nodes: ");
    scanf("%d", &n);
    int x[n];
    printf("Enter the values of those nodes: ");
    for (int i = 0; i < n; i++)
    {
        scanf("%d", &x[i]);
    }
    for (int i = n-1; i >= 0; i--)
    {
        insert(x[i]);
    }
    printf("Linked list before reversing is as follows:\n");
    display();

    reverse();
    printf("\nLinked list after reversing is as follows:\n");
    display();
    return 0;
}
```