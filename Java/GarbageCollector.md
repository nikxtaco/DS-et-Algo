# Garbage Collector

## Q. Demonstrate the use of garbage collector. 
```
public class Main
{
   public static void main(String[] args)
   {
      Main i = new Main();
      i = null;
      System.gc();
   }
   public void finalize()
   {
      System.out.println("Garbage Collection is done.");
   }
}
```
