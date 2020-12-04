# Linear Search

## Linear Search (Iterative)
```
#include<stdio.h>
 
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
#include<stdio.h>
 
int linearSearch(int arr[], int l, int r, int x)
{
    if (r < l)
       return -1;
    if (arr[l] == x)
       return l;
    if (arr[r] == x)
       return r;
    return linearSearch(arr, l+1, r-1, x);
}

int main()
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
   int index = linearSearch(arr, 0, n-1, x) + 1;
   
   if (index != -1)
      printf("Element %d is present at index %d", x, index);
   else
       printf("Element %d is not present", x);
   return 0;
}
```
