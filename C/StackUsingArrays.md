# Stack

## Q. Double Array: Design a method for keeping two stacks with in a single linear array so that neither stacks overflow until all the memory is used, i.e., one grows from one side of the array and the other grows from the other side.

```
#include <stdio.h>

int a[100], top1 = -1, top2 = 100;

void pushToOne(){
    if (top1<top2){
        printf("Enter value to push to stack: ");
        int num;
        scanf("%d", &num);
        a[++top1] = num;
    }
    else printf("Stack 1 is full.\n");
}

void popOne(){
    if (top1>-1){
        printf("%d was popped.\n", a[top1]);
        top1--;
    }
    else printf("Stack 1 is empty.\n");
}

void displayOne(){
    if (top1 > -1)
    {
      printf("Stack 1: ");
      for(int i=0;i<=top1;i++)
      printf("%d ", a[i]);
      printf("\n");
    }
    else printf("Stack 1 is empty.\n");
}

void pushToTwo(){
    if (top2>top1)
    {
        printf("Enter value to push to stack: ");
        int num;
        scanf("%d", &num);
        a[--top2] = num;
    }
    else printf("Stack 2 is full.\n");
}

void popTwo(){
    if(top2<100){
        printf("%d was popped.\n", a[top2]);
        top2++;
    }
    else printf("Stack 2 is empty.\n");
}

void displayTwo(){
    if(top1<100)
    {
      printf("Stack 2: ");
      for(int i=99;i>=top2;i--)
      printf("%d ", a[i]);
      printf("\n");
    }
    else printf("Stack 2 is empty.\n");
}

int main()
{
    int ch = 0;
    do{
      printf("\n1) Push to stack 1\n2) Pop from stack 1\n3) Display stack 1\n4) Push to stack 2\n5) Pop from stack 2\n6) Display stack 2\n7) Exit\nEnter your choice: ");
      scanf("%d", &ch);
      switch (ch)
      {
      case 1: pushToOne(); break;
      case 2: popOne(); break;
      case 3: displayOne(); break;
      case 4: pushToTwo(); break;
      case 5: popTwo(); break;
      case 6: displayTwo(); break;
      }
    }while (ch < 7);

    return 0;
}
```
