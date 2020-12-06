# Multithreading

## Q. Create two threads: One for displaying all odd numbers between 1 and 100 and another for displaying all even numbers between 1 and 100.
```
class OddThread implements Runnable{
 public void run(){
   try{
     for(int i=1;i<100;i=i+2){
       System.out.print("Odd: " + i + " ");
       Thread.sleep(500);
     }
   }
   catch(InterruptedException e){
     System.out.println("Odd Thread Interrupted "+e);
   }
   System.out.println("\nExiting Odd Thread");
 }
}
 
class EvenThread implements Runnable{
 public void run(){
   try{
     for(int i=2;i<=100;i=i+2){
       System.out.print("Even: " + i + "\n");
       Thread.sleep(500);
     }
   }
   catch(InterruptedException e){
     System.out.println("Even Thread Interrupted "+e);
   }
   System.out.println("\nExiting Even Thread");
 }
}
 
class Main{
 public static void main(String args[]){
   Thread t1 = new Thread(new OddThread(), "odd");
   Thread t2 = new Thread(new EvenThread(), "even");
   t1.start();
   t2.start();
   try{
     Thread.sleep(40500);
   }
   catch(InterruptedException e){
     System.out.println("Main Thread Interrupted "+e);
   }
   System.out.println("\nExiting Main Thread");
 }
}
```
