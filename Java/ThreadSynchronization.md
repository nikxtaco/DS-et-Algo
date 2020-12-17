# Thread Synchronization

## Q. Write a Java program that shows thread synchronization.
```
class Table
{  
    synchronized void printTable(int n)
    {
        for(int i=1;i<=5;i++)
        {  
            System.out.println(n*i);  
            try
            {  
                Thread.sleep(1000);  
            }
            catch(Exception e)
            {
                System.out.println(e);
            }  
        }  
    }  
}  

class Thread1 implements Runnable
{  
    Table t;  
    Thread1(Table t)
    {  
        this.t=t; 
    }  
    public void run()
    {  
        t.printTable(2);  
    }  
}  

class Thread2 implements Runnable
{  
    Table t;  
    Thread2(Table t)
    {  
        this.t=t;  
    }  
    public void run()
    {  
        t.printTable(10);  
    }  
}  

class Main
{  
    public static void main(String args[])
    {  
        Table obj = new Table(); 
        Thread t1=new Thread(new Thread1(obj), "Two's");  
        Thread t2=new Thread(new Thread2(obj), "Ten's");
        t1.start();  
        t2.start();  
    }  
}
```
