# Binary Search

#### Q. Program to implement Binary search in Java.
```
import java.util.*;

class Main
{
    void insert(int arr[])
    {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter the elements of the array:");
        for(int i=0;i<arr.length;i++)
        arr[i] = sc.nextInt();
    }

    void bubble(int arr[])
    {
        int temp;
        for(int i=0;i<arr.length-1;i++)
        {
            for(int j=0;j<arr.length-1-i;j++)
            {
                if(arr[j]>arr[j+1])
                {
                    temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    } 

    int binarySearch(int arr[], int elem)
    {
        int mid,l,u,pos;
        l = 0;
        u = arr.length - 1;
        pos = -1;
        
        while(l <= u)
        {
            mid = l + (u-l)/2;
            if(arr[mid] > elem)
                u = mid - 1;
            else if(arr[mid] < elem)
                l = mid + 1;
            else
            {
                pos = mid;
                break;
            }
        }
        return pos;
    }

    void display(int arr[]) 
    {
        System.out.print("The contents of the array after sorting: ");
        for(int i=0;i<arr.length;i++)
            System.out.print(arr[i] + "  ");
        System.out.println();
    }

    public static void main(String args[])
    {
        binary b1 = new binary();
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter the number of elements to be stored: ");
        int n = sc.nextInt();

        int arr[] = new int[n];
        b1.insert(arr);
        b1.bubble(arr);
        b1.display(arr);

        System.out.print("Enter the element to search: ");
        int x = sc.nextInt();

        int res = b1.binarySearch(arr, x);
        if(res == -1)
            System.out.println("The element " + x + " was not found in the array.");
        else
            System.out.println("The element " + x + " was found in the array at position " + (res+1) + ".");
    }
}
```
