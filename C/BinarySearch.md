# Linear Search

## Linear Search (Iterative)
```
#include <stdio.h>
 
int binarySearch(int arr[], int l, int r, int x)
{
   while (l <= r) {
       int m = l + (r - l) / 2;
 
       if (arr[m] == x)
           return m;
       if (arr[m] < x)
           l = m + 1;
       else
           r = m - 1;
   }
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
   int result = binarySearch(arr, 0, n - 1, x) + 1;
   (result == -1) ? printf("Element is not present"
                           " in array")
                  : printf("Element is present at "
                           "index %d",
                           result);
   return 0;
}
```
## Linear Search (Recursive)
```
#include <stdio.h>
 
int binarySearch(int arr[], int l, int r, int x)
{
   if (r >= l) {
       int mid = l + (r - l) / 2;
        if (arr[mid] == x)
           return mid;
       if (arr[mid] > x)
           return binarySearch(arr, l, mid - 1, x);
       return binarySearch(arr, mid + 1, r, x);
   }
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
   int result = binarySearch(arr, 0, n - 1, x) + 1;
   (result == -1) ? printf("Element is not present in array")
                  : printf("Element is present at index %d",
                           result);
   return 0;
}
```
