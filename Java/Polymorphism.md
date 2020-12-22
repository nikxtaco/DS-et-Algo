# Polymorphism Using Classes 

#### Q1. reate an abstract class named Shape that contains an empty method named numberOfSides( ). Provide three classes named Rectangle, Triangle and Hexagon such that each one of the classes extends the class Shape. Each one of the classes contains only the method numberOfSides( ) that shows the number of sides in the given geometrical structures.
```
abstract class Shape
{
   abstract void numberOfSides();
}
 
class Rectangle extends Shape
{
   void numberOfSides()
   {
       System.out.println("\nA Rectangle has 2 sides.");
   }
}
 
class Hexagon extends Shape
{
   void numberOfSides()
   {
       System.out.println("\nA Hexagon has 6 sides.");
   }
}
 
class Triangle extends Shape
{
   void numberOfSides()
   {
       System.out.println("\nA Triangle has 3 sides.");
   }
}
 
class Main
{
  public static void main(String Args[])
  {
     Rectangle ek1 = new Rectangle();
     Triangle do2 = new Triangle();
     Hexagon teen3 = new Hexagon();
    
     ek1.numberOfSides();
     do2.numberOfSides();
     teen3.numberOfSides();
 }
}
```
