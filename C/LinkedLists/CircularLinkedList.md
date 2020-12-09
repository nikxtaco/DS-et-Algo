# Cicular Linked List

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

int insert_particular(int elem, int item)
{
    struct list *node,*start;
    node = malloc(sizeof(struct list));
    node->data = item;
    node->link = NULL;
    start = loc;
    int flag = 0;

    do
    {
        if(loc->link == NULL && loc->data == elem)
        {
            node->link = loc;
            loc->link = node;
            flag = 1;
            break;
        }
        else if(loc->data == elem)
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

int delete_particular(int elem)
{
    struct list *prev,*start;
    start = loc;
    prev = loc;
    if(loc->link == NULL && loc->data == elem)
    {
        loc = NULL;
        return 1;
    }
    loc = loc->link;
    while(loc != start && loc->data != elem)
    {
        prev = loc;
        loc = loc->link;
    }
    if(loc->data == elem)
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

void display_list()
{
    struct list *node;
    node = loc;
    printf("\nThe contents in the Linked List are: ");
    while(node->link != loc)
    {
        printf("%d  ", node->data);
        node = node->link;
    }
    printf("%d  ", node->data); 
    printf("\n");
}

int main()
{
    int n,ch,x,pos,res;
    printf("Enter the first element of the Linked List: ");
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
        printf("\n1. Insert node at a certain position");
        printf("\n2. Delete node containing a certain value");
        printf("\n3. Exit");
        printf("\nEnter you choice: ");
        scanf("%d",&ch);

        switch(ch)
        {
            case 1: printf("Enter the node after which the new node is to be inserted: ");
                    scanf("%d", &pos);
                    printf("Enter the element to be inserted: ");
                    scanf("%d",&x);
                    int y = insert_particular(pos,x);
                    if(y == 1)
                    {
                        printf("Element was inserted succesfully");
                        num++;
                    }
                    else
                        printf("The element %d was not found; Insertion Unsuccessful",pos);
                    display_list();
                    break;
            case 2: printf("Enter the particular item to be deleted: ");
                    scanf("%d",&x);
                    res = delete_particular(x);
                    if(res == 1)
                    { 
                        printf("Node with the element %d was deleted succesfully\n",x);
                        num--;
                        if(num != 0)
                            display_list();
                        else
                        {
                            printf("The list is empty now!\nEnter a new element to continue: ");
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
                        printf("Deletion was unsuccesful since no node has the value: %d\n",x);
                    break;
            case 3: break;
            default: printf("Invalid choice.\n");
        }
    }while(ch != 3);
    
    return 0;
}
```