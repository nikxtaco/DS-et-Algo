# Reverse A String

### Q. Display the reverse of a given string.
```
public class Main 
{
   public static void main(String[] args)
   {
       String str = "abc xyz";
       StringBuilder str1 = new StringBuilder();
       str1.append(str);
       str1 = str1.reverse();
       System.out.println(str + " reversed is " + str1);
   }
}
```
