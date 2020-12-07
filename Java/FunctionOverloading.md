# Function Overloading

### Q. Calculate the area of different shapes namely circle, rectangle, and triangle using the concept of method overloading.
```
class Main
{
   void calculateArea(float x)
   {
       System.out.println("Area of the square: "+x*x+" sq units");
   }
   void calculateArea(float x, float y)
   {
       System.out.println("Area of the rectangle: "+x*y+" sq units");
   }
   void calculateArea(double r)
   {
       double area = 3.14*r*r;
       System.out.println("Area of the circle: "+area+" sq units");
   }
   public static void main(String args[])
   {
      AreaClass obj = new AreaClass();
      obj.calculateArea(21.5f);
      obj.calculateArea(15,18);
      obj.calculateArea(6.4);
   }
}
```
