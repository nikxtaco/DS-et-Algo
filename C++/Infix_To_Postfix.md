# Infix, Postfix & Prefix

## Q. Write a program in C to convert a given infix expression to postfix form.

```
#include <stdio.h>
#include <ctype.h>

char stack[100];
int top = -1;

void push(char x){
    stack[++top]=x;
}

int pop(){
    if(top==-1)
    return -1;
    else
    return stack[top--];
}

int PriorityOfOperator(char x){
    if (x == '(')
        return 1;
    else if (x == '+' || x == '-')
        return 2;
    else if (x == '*' || x == '/')
        return 3;
    else 
        return 0;
}

int main()
{
    char exp[100];
    char x;
    printf("Enter the infix expression: ");
    scanf("%s", exp);

    printf("\nThe postfix expression is: ");

    for (char *xp=exp; *xp != '\0'; xp++)
    {
        if (isalnum(*xp))
            printf("%c", *xp);
        else if (*xp == '(')
            {
              push(*xp);
            }
        else if (*xp == ')'){
            while ((x = pop()) != '(')
            printf("%c", x);
        }
        else{
            while(PriorityOfOperator(stack[top]) >= PriorityOfOperator(*xp))
              printf("%c", pop());
            push(*xp);
        }
    }

    while (top != -1)
        printf("%c", pop());

    return 0;
}
```
