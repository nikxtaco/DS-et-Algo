# Inheritance

#### Q1. Write two Java classes Employee and Engineer. Engineer should inherit from Employee class. Employee class should have two methods - display() and calcSalary(). Write a program to display the engineer's salary and to display from Employee class using a single object instantiation. display() only prints the name of the class and does not return any value. Ex. “Name of class is Employee” calcSalary() in Employee displays “Salary of employee is 10000” and calcSalary() in Engineer displays “Salary of employee is 20000".
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
 
class Engineer extends Employee
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
#### Q2. Write two Java classes Employee and Engineer. Engineer should inherit from Employee class. Employee class to have two methods - display() and calcSalary(). Write a program to display the engineer's salary and to display from Employee class using a single object instantiation. display() only prints the name of the class and does not return any value. Ex. “Name of class is Employee.” calcSalary() in Employee displays “Salary of employee is 10000.” and calcSalary() in Engineer displays “Salary of employee is 20000.".
```
###In Employee.java:
 
public class Employee
{  
   public int age;
   public long salary;
   public String name, address, phoneNumber;
 
   public void printSalary() 
   {
       System.out.println("Salary - " + salary);
   }
}
 
###In Manager.java:
 
public class Manager extends Employee
{
   public String department;
}
 
###In Officer.java:
 
import java.util.List;
public class Officer extends Employee
{
   public String specialization;
}
 
###In Main.java:
 
class Main
{
   public static void main(String[] args)
   {
       Officer off = new Officer();
       Manager mgr = new Manager();
 
       off.name = "Miranda Sings";
       off.age = 22;
       off.phoneNumber = "5454545454";
       off.address = "22/7 Strangers Street";
       off.salary = 535354;
       mgr.name = "Miranda Sings deux";
       mgr.age = 24;
       mgr.phoneNumber = "3434343434";
       mgr.address = "22/7 Familiar Street";
       mgr.salary = 5353540;
       
       System.out.println("\nOfficer: \n" + "Name - " + off.name + "\nAge - " + off.age + "\nPhone Number - " + off.phoneNumber + "\nAddress - " + off.address + "\n");
       off.printSalary();
 
       System.out.println("\nManager: \n" + "Name - " + mgr.name + "\nAge - " + mgr.age + "\nPhone Number - " + mgr.phoneNumber + "\nAddress - " + mgr.address );
       mgr.printSalary();
   }
}
```
