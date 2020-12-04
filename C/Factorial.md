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
# Fibonacci Series

## Fibonacci Series Of N Numbers (Iterative)
```
#include <stdio.h>

int main(void) 
{
  unsigned long long n1=0,n2=1,n3,i,x;  
  printf("Enter the number of elements: ");  
  scanf("%llu",&x);  
  printf("The Fibonacci sequence is: %llu %llu",n1,n2);
  
  for(i=2;i<x;++i)
  {  
    n3=n1+n2;  
    printf("%llu",n3);  
    n1=n2;  
    n2=n3;  
  }
  return 0;
}
```
## Fibonacci Series Of N Numbers (Recursive)
```
#include <stdio.h>

void Fibonacci(int n)
{  
  static unsigned long long n1=0,n2=1,n3;  
  if(n>0)
  {  
       n3 = n1 + n2;  
       n1 = n2;  
       n2 = n3;  
       printf("%llu ",n3);  
       Fibonacci(n-1);  
  }  
}  

int main(void) 
{
  unsigned long long n;  
  printf("Enter the number of elements: ");  
  scanf("%llu",&n);  
  printf("The Fibonacci Series is: ");  
  printf("%d %d ",0,1);  
  Fibonacci(n-2);
  return 0;
}
```
