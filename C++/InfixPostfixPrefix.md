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

## Q. Write a program in C to evaluate a given postfix expression.

```
#include <stdio.h>
#include <ctype.h>

int stack[100];
int top = -1;

void push(int x){
    stack[++top]=x;
}

int pop(){
    return stack[top--];
}

int main()
{
    char exp[100];
    int x1, x2, x3, num;
    printf("Enter postfix expression: ");
    scanf("%s", exp);

    for (char *xp = exp; *xp != '\0'; xp++)
    {
        if(isdigit(*xp))
        {
            num = *xp - 48;
            push(num);
        }
        else
        {
            x1 = pop();
            x2 = pop();
            switch (*xp){
              case '+': x3 = x1 + x2;
                        break;
              case '-': x3 = x2 - x1;
                        break;
              case '*': x3 = x1 * x2;
                        break;
              case '/': x3 = x2 / x1;
                        break;
            }
            push(x3);
        }
    }

    printf("Answer: %d\n", pop());

    return 0;
}
```
