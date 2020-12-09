# Doubly Linked List

### Q. Implement a doubly linked list and to perform the following: Insert a node at the beginning of the list, insert a node after a particular node in the list, insert a node at the end of the list, delete a node containing a particular item.
```
#include<stdio.h>
#include<stdlib.h>

struct list{
    int data;
    struct list *prev;
    struct list *next;
};

struct list *start;

void DisplayList()
{
    struct list *node;
    node = start;
    printf("The contents of the Linked List are: ");
    while(node!=NULL)
    {
        printf("%d  ",node->data);
        node = node->next;
    }
    printf("\n");
}

void InsertBegin(int element)
{
    struct list *node;
    node = malloc(sizeof(struct list));
    node->data = element;
    node->next = NULL;
    node->prev = NULL;

    if(start!=NULL)
    {
        node->next = start;
        start->prev = node;
    }
    start = node;
    printf("Element inserted succesfully.\n");
    
    DisplayList();
}

void InsertEnd(int element)
{
    struct list *node;
    node = malloc(sizeof(struct list));
    node->data = element;
    node->next = NULL;
    node->prev = NULL;

    struct list *temp;
    temp = start;

    while(temp->next != NULL)
        temp = temp->next;

    temp->next = node;
    node->prev = temp;
    printf("Element inserted succesfully.\n");

    DisplayList();
}

//For any position between beginning and end excluding the first position
void InsertAtPos(int element, int pos)
{
    struct list *node;
    node = malloc(sizeof(struct list));
    node->data = element;
    node->next = NULL;
    node->prev = NULL;

    struct list *temp;
    temp = start;
    int i=1;

    while(i < pos)
    {
        temp = temp->next;
        i++;
    }

    node->next = temp->next;
    temp->next->prev = node;
    temp->next = node;
    node->prev = temp;
    printf("Element inserted succesfully after node %d.\n",pos);
        
    DisplayList();
}

int DeleteNode(int element)
{
    struct list *loc,*prev;
    loc = start;

    while(loc!=NULL && loc->data!=element)
        loc = loc->next;

    if(loc==start && loc->next!=NULL)
    {
        start = start->next;
        start->prev = NULL;
        return 1;
    }
    if(loc==start && loc->next == NULL)
    {
        start = NULL;
        loc = NULL;
        return 1;
    }
    if(loc->next==NULL)
    {
        loc->prev->next = NULL;
        return 1;
    }
    if(loc!=NULL)
    {
        loc->prev->next = loc->next;
        loc->next->prev = loc->prev;
        return 1;
    }
    else
    {
        printf("Element not found.\n");
        return 0;
    }
}

int main()
{
    int n,ch,x,pos,res;
    printf("Enter the first element of the Linked List: ");
    scanf("%d",&n);
    start = NULL;
    struct list *newnode;
    newnode = malloc(sizeof(struct list));
    newnode->data = n;
    newnode->next = NULL;
    newnode->prev = NULL;

    if(start == NULL)
        start = newnode;

    int num = 1;
    do {
        printf("\n1. Insert node at the beginning.");
        printf("\n2. Insert node at the end.");
        printf("\n3. Insert node at a certain position.");
        printf("\n4. Delete node containing a certain value.");
        printf("\n5. Exit.");
        printf("\nEnter your choice: ");
        scanf("%d",&ch);

        switch(ch)
        {
            case 1: printf("Enter the element to be inserted: ");
                    scanf("%d",&x);
                    InsertBegin(x);
                    num++;
                    break;
            case 2: printf("Enter the element to be inserted: ");
                    scanf("%d",&x);
                    InsertEnd(x);
                    num++;
                    break;
            case 3: printf("Enter the number of nodes after which the new node is to be inserted: ");
                    scanf("%d", &pos);
                    if(num >= pos)
                    {
                        printf("Enter the element to be inserted: ");
                        scanf("%d",&x);
                        InsertAtPos(x,pos);
                        num++;
                    }
                    else
                        printf("Element cannot be inserted after position %d since there aren't enough nodes yet\n",pos);
                    break;
            case 4: printf("Enter the particular item to be deleted: ");
                    scanf("%d",&x);
                    res = DeleteNode(x);
                    if(res == 1)
                    { 
                        printf("Node with element %d deleted succesfully.\n",x);
                        num--;
                        if(num != 0)
                        DisplayList();
                        else
                        printf("The list is empty now.\n");
                    }
                    break;
            case 5: break;
            default: printf("Invalid choice.\n");
        }
    }while(ch != 5);
    return 0; 
}
```