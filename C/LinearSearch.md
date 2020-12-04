# Linear Search

## Linear Search (Iterative)
```
#include <stdio.h>
 
int linearsearch(int arr[], int n, int x)
{
   int i;
   for (i = 0; i < n; i++)
       if (arr[i] == x)
           return i;
   return -1;
}

int main(void)
{
   int n,x;
   printf("Enter the number of elements in your array: ");
   scanf("%d",&n);
   printf("Enter your array: ");
   int arr[n];
   
   for(int i=0;i<n;i++)
      scanf("%d", &arr[i]);
   printf("Enter the number you want to search for: ");
   scanf("%d",&x);
   
   int result = linearsearch(arr, n, x) + 1;
   (result == -1) ? printf("Element is not present in array")
                  : printf("Element is at index %d", result);
   return 0;
}
```
## Linear Search (Recursive)
```

```
