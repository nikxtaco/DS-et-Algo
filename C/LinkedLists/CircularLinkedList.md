# Circular Linked List

### Q. Implement a circular linked list.
```
#include<stdlib.h>
#include<stdio.h>

struct list {
    int data;
    struct list *link;
};

struct list *loc;
int num = 0;

int InsertNode(int element, int item)
{
    struct list *node,*start;
    node = malloc(sizeof(struct list));
    node->data = item;
    node->link = NULL;
    start = loc;
    int flag = 0;

    do
    {
        if(loc->link == NULL && loc->data == element)
        {
            node->link = loc;
            loc->link = node;
            flag = 1;
            break;
        }
        else if(loc->data == element)
        {
            node->link = loc->link;
            loc->link = node;
            flag = 1;
            break;
        }
        loc = loc->link;
    }while(loc != start);

    loc = start;
    return flag;
}

int DeleteNode(int element)
{
    struct list *prev,*start;
    start = loc;
    prev = loc;
    if(loc->link == NULL && loc->data == element)
    {
        loc = NULL;
        return 1;
    }
    loc = loc->link;
    while(loc != start && loc->data != element)
    {
        prev = loc;
        loc = loc->link;
    }
    if(loc->data == element)
    {
        if(loc == start)
            start = NULL;
        prev->link = loc->link;
        if(start != NULL)
            loc = start;
        else
            loc = prev->link;
        return 1;
    }
    else
        return 0;
}

void Display()
{
    struct list *node;
    node = loc;
    printf("\nThe contents of the Linked List are: ");
    while(node->link != loc)
    {
        printf("%d  ",node->data);
        node = node->link;
    }
    printf("%d  ",node->data); 
    printf("\n");
}

int main()
{
    int n,ch,x,elt,ans;
    printf("Enter the first element of the Circular Linked List: ");
    scanf("%d",&n);
    loc = NULL;
    struct list *newnode;
    newnode = malloc(sizeof(struct list));
    newnode->data = n;
    newnode->link = NULL;

    if(loc == NULL)
    loc = newnode;
    num++;

    do
    {
        printf("\n1. Insert node after a certain element.");
        printf("\n2. Delete node containing a certain element.");
        printf("\n3. Exit.");
        printf("\nEnter your choice: ");
        scanf("%d",&ch);

        switch(ch)
        {
            case 1: printf("\nEnter the element after which the new element is to be inserted: ");
                    scanf("%d", &elt);
                    printf("Enter the element to be inserted: ");
                    scanf("%d",&x);
                    int y = InsertNode(elt,x);
                    if(y == 1)
                    {
                        printf("Element inserted succesfully.");
                        num++;
                    }
                    else
                        printf("The element %d was not found.",elt);
                    Display();
                    break;
            case 2: printf("\nEnter the element to be deleted: ");
                    scanf("%d",&x);
                    ans = DeleteNode(x);
                    if(ans == 1)
                    { 
                        printf("Node with the element %d deleted succesfully.\n",x);
                        num--;
                        if(num != 0)
                            Display();
                        else
                        {
                            printf("The list is empty.\nEnter a new element to proceed: ");
                            scanf("%d",&n);
                            loc = NULL;
                            struct list *newnode;
                            newnode = malloc(sizeof(struct list));
                            newnode->data = n;
                            newnode->link = NULL;
                            if(loc == NULL)
                            loc = newnode;
                            num++;     
                        }
                    }
                    else
                        printf("\nNo node has the value %d.\n",x);
                    break;
            case 3: break;
            default: printf("Invalid choice.\n");
        }
    }while(ch != 3);
    
    return 0;
}
```