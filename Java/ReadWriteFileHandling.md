# Error Handling

## Q. Write a Java program that shows the usage of try, catch, throws and finally.
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
