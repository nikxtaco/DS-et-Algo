# Inheritance

#### Q1. Write two Java classes Employee and Engineer. Engineer should inherit from Employee class. Employee class to have two methods - display() and calcSalary(). Write a program to display the engineer's salary and to display from Employee class using a single object instantiation. display() only prints the name of the class and does not return any value. Ex. “Name of class is Employee.” calcSalary() in Employee displays “Salary of employee is 10000.” and calcSalary() in Engineer displays “Salary of employee is 20000.".
```
class Employee
{
    public void display()
    {
        System.out.println("Name of class is Employee."); 
    }
    public void calcSalary()
    {
        System.out.println("Salary of employee is 10000."); 
    }
}
 
class  Engineer extends Employee
{
    public void calcSalary()
    {
        super.display();
        super.calcSalary();
        System.out.println("Salary of employee is 20000."); 
    }
}
 
public class Main
{
   public static void main(String[] args)
   {
       Engineer objecc= new Engineer();
       objecc.calcSalary();
   }
}
```
