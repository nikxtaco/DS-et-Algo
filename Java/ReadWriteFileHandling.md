# Error Handling

## Q1. Write a Java program that shows the usage of try, catch, throws and finally.
```
public class Main
{
    public static void main(String args[]) throws ArrayIndexOutOfBoundsException
    {
        try
        {
            int a[] = new int[6];
            System.out.println("Accessing element 7: " + a[7]);
        }
        catch (ArrayIndexOutOfBoundsException e)
        {
            System.out.println("Exception thrown: " + e);
        }
        finally
        {
            System.out.println("Finally has been performed.");
        }
    }
}
```
## Q2. Write a Java program that shows the usage of try, catch, throws and finally. Write a java program to read a set of strings from the keyboard and display the sorted strings in ascending order. (String input can be stopped by entering "end" as the last string). Perform sorting independent of case of letters.
```
public class Main
{
    public static void main(String args[]) throws ArrayIndexOutOfBoundsException
    {
        try
        {
            int a[] = new int[6];
            System.out.println("Accessing element 7: " + a[7]);
        }
        catch (ArrayIndexOutOfBoundsException e)
        {
            System.out.println("Exception thrown: " + e);
        }
        finally
        {
            System.out.println("Finally has been performed.");
        }
    }
}
```
