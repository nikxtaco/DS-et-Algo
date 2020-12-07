# Second Smallest Element

### Q. Find the second smallest element in an array.
```
class Main {
 public static void main(String[] args) {
 
   int a[]={1,4,3,4};
   int min=a[0], min2=a[0];
 
   int temp; 
   for (int i = 0; i < 4; i++)  
       { 
           for (int j = i + 1; j < 4; j++)  
           { 
               if (a[i] > a[j])  
               { 
                   temp = a[i]; 
                   a[i] = a[j]; 
                   a[j] = temp; 
               } 
           } 
       } 
 
   System.out.println("The Second Smallest element is " + a[1]);
 
 }
}
```
