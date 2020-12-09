# Polynomial Addition

## Polynomial Addition Using Linked List
```
#include <stdio.h>

#define max 5
int a[max], front = -1, rear = -1;

void enqueue(){
    if ((front == 0 && rear == max-1) || (rear + 1 == front))
        printf("Queue is full.\n");
    else{
        int val;
        printf("Enter value to add to queue: ");
        scanf("%d", &val);
        if (front == -1)
            front = rear = 0;
        else if (rear == max-1)
            rear = 0;
        else
            rear++;
        a[rear] = val;
    }
}

void dequeue(){
    if (front == -1)
    printf("Queue is empty.\n");
    else{
        printf("%d has been removed.\n", a[front]);
        if (front == rear)
            front = rear = -1;
        else if (front == max-1)
            front = 0;
        else
            front++;
    }
}

void display(){
  if (rear == -1)
    printf("Queue is empty.\n");
    else{
        int i=front;
        printf("The Queue is:\n");
        if(rear<front){
          for(;i<max;i++)
          printf("%d ", a[i]);
          i=0;
        }
        for(;i<=rear;i++)
        printf("%d ", a[i]);
        printf("\n");
    }
}

int main(){
    int ch = 0;
    do{
      printf("\n1) Add to queue\n2) Remove from queue\n3) Display queue\n4) Exit\nEnter your choice: ");
      scanf("%d", &ch);
      switch (ch)
      {
      case 1: enqueue(); break;
      case 2: dequeue(); break;
      case 3: display(); break;
      }
    }while (ch < 4);

    return 0;
}
```