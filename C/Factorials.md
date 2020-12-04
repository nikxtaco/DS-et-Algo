# Factorials

## Factorial Of N Numbers (Iterative)
```
#include <stdio.h>
 
int main(void) 
{
   int n, i;
   unsigned long long fact = 1;
   printf("Enter an integer: ");
   scanf("%d", &n);
 
   if(n<0)
       printf("Only positive numbers are acceptable.");
   else
   {
       for (i = 2; i <= n; ++i)
           fact *= i;
       
       printf("Factorial of %d = %llu", n, fact);
   }
 
 return 0;
}
```
## Factorial Of N Numbers (Recursive)
```
#include <stdio.h>
 
long int fact(int n) 
{
   if (n>=1)
       return n*fact(n-1);
   else
       return 1;
}
 
int main(void) 
{
   int n;
   printf("Enter a positive integer: ");
   scanf("%d",&n);
   printf("Factorial of %d = %ld", n, fact(n));
   return 0;
}
```
