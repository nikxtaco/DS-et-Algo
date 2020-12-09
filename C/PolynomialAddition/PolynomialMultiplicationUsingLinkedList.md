# Polynomial Multiplication

## Polynomial Multiplication Using Linked List
```
#include<stdio.h>
#include<stdlib.h>

struct node
{
	int coeff;
	int exp;
	struct node *link;
} *start=NULL,*startb=NULL,*startc=NULL;

void insert(struct node **p,int m,int n)
{
	struct node *loc;
	struct node *newnode=malloc(sizeof(struct node));
	newnode->coeff=m;
	newnode->exp=n;
	newnode->link=NULL;
	loc=(*p);
	if((*p)==NULL)
	{
		newnode->link=(*p);
		(*p)=newnode;
	}
	else
	{
		while(loc->link!=NULL)
		loc=loc->link;
		loc->link=newnode;	
	}
}
void display(struct node *p)
{  
	struct node *loc;
	loc=p;
	
	while(loc->link!=NULL)
	{
		printf("%dx^%d +",loc->coeff ,loc->exp);
		loc=loc->link;
	}
	printf("%dx^%d ",loc->coeff ,loc->exp);
}
void multiply(int a,int b)
{
	int i,j;
	struct node *loc;
	struct node *temp;
	loc=start;
	i=0;
	while(i<a)
	{   temp=startb;
	    j=0;
		while(j<b)
		{
			insert(&startc,(loc->coeff*temp->coeff),loc->exp+temp->exp);
			temp=temp->link;
			j++;
		}
		loc=loc->link;
		i++;
	}

	loc=startc;
	while(loc->link!=NULL)
	{ 
        if(loc->exp==loc->link->exp)
        {  
            loc->coeff=loc->coeff+loc->link->coeff;
            loc->link=loc->link->link;
        }
        loc=loc->link;
	}
}

int main()
{
	int a,b,t1,t2,i;
	printf("Enter the number of terms of 1st polynomial: ");
	scanf("%d",&a);

	for(i=0;i<a;i++)
	{
	  printf("Enter coefficient %d: ",i+1);
		scanf("%d",&t1);
		printf("Enter exponent %d: ",i+1);
		scanf("%d",&t2);
		insert(&start,t1,t2);
	}
	printf("\nThe 1st polynomial is: ");
	display(start);

  printf("\n\nEnter the number of terms of 2nd polynomial: ");
	scanf("%d",&b);

	for(i=0;i<b;i++)
	{
		printf("Enter coefficient %d: ",i+1);
		scanf("%d",&t1);
		printf("Enter exponent %d: ",i+1);
		scanf("%d",&t2);
		insert(&startb,t1,t2);
	}
	printf("\nThe 2nd polynomial is: ");
	display(startb);

	printf("\n\nThe product of the two polynomials is: ");
	multiply(a,b);
	display(startc);

    return 0;
}
```