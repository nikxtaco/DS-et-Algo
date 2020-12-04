# Polynomial Addition

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
Q3) Write a program in C to print the Fibonacci series upto n numbers
without using recursion.
```
#include < stdio.h >
int main( void ) {
int n1= 0 ,n2= 1 ,n3,i,x;
printf( "Enter the number of elements: " );
scanf( "%d" ,&x);
printf( "The Fibonacci sequence is: %d %d" ,n1,n2);
for (i= 2 ;i<x;++i)
{
n3=n1+n2;
printf( " %d" ,n3);
n1=n2;
n2=n3;
}
return 0 ;
}
```
Q4) Write a program in C to print the Fibonacci series upto n numbers
using recursion.
```
#include < stdio.h >
void Fibonacci( int n){
static int n1= 0 ,n2= 1 ,n3;
if (n> 0 ){
n3 = n1 + n2;
n1 = n2;
n2 = n3;
printf( "%d " ,n3);
Fibonacci(n- 1 );
}
}
int main( void ) {
int n;
printf( "Enter the number of elements: " );
scanf( "%d" ,&n);
printf( "The Fibonacci Series is: " );
printf( "%d %d " , 0 , 1 );
Fibonacci(n- 2 );
return 0 ;
}
```
