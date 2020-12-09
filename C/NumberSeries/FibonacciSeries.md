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
