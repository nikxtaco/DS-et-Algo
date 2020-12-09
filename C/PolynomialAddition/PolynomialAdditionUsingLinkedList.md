# Polynomial Addition

## Polynomial Addition Using Linked List
```
#include<stdio.h>
#include<stdlib.h>

struct node
{
	int coeff;
	int expo;
	struct node *link;
} *start=NULL,*startb=NULL,*startc=NULL;

void display(struct node *p)
{  
	struct node *loc=NULL;
	loc=p;
	
	while(loc->link!=NULL)
	{
		printf("%dx^%d +",loc->coeff ,loc->expo);
		loc=loc->link;
	}
	printf("%dx^%d ",loc->coeff ,loc->expo);
}

void insert(struct node **p,int m,int n)
{
	struct node *loc;
	struct node *newnode=malloc(sizeof(struct node));
	newnode->coeff=m;
	newnode->expo=n;
	newnode->link=NULL;
    loc=*p;
	
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

void sum(struct node *loc,struct node *temp)
{   
	struct node *newnode=malloc(sizeof(struct node));
	int m;
	while(loc->link!=NULL && temp->link!=NULL)
	{  
		if(loc->expo>temp->expo)
		{
			insert(&startc,loc->coeff,loc->expo);
			loc=loc->link;
		}
		else if(loc->expo<temp->expo)
		{
			insert(&startc,temp->coeff,temp->expo);
			temp=temp->link;
		}
		else 
		{
		    m=loc->coeff+temp->coeff;
		    insert(&startc,m,temp->expo);
			loc=loc->link;
			temp=temp->link;
		}
	}
	while(loc->link!=NULL && temp->link==NULL)
    {
    	if(loc->expo==temp->expo)
    	{
    		insert(&startc,temp->coeff+loc->coeff,temp->expo);
    		loc=loc->link;
		}
		else
		{
				insert(&startc,loc->coeff,loc->expo);
				loc=loc->link;
		}
	}
	while(loc->link==NULL && temp->link!=NULL)
	{
		if(temp->expo==loc->expo)
		{
			insert(&startc,temp->coeff+loc->coeff,temp->expo);
			temp=temp->link;
		}
		else
		{
			insert(&startc,temp->coeff,temp->expo);
			temp=temp->link;
		}
	}
	if(temp->expo==loc->expo)
	insert(&startc,temp->coeff+loc->coeff,temp->expo);
	else if(temp->expo>loc->expo)
	{
        insert(&startc,temp->coeff,temp->expo);
		insert(&startc,loc->coeff,loc->expo);
	}
	else
	{
        insert(&startc,loc->coeff,loc->expo);
        insert(&startc,temp->coeff,temp->expo);
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

	sum(start,startb);
	printf("\n\nThe sum of the two polynomials is: ");
  display(startc);

  return 0;
}
```