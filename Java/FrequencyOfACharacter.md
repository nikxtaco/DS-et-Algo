# Frequency Of A Character

#### Q. Find the frequency of a given character in a string.
```
public class Main 
{
   static int Frequency(String str, char x)
   {
       int count = 0;
       for(int i = 0; i<str.length()-1; i++)
       {
         if(str.charAt(i) == x)
         count++;
       }
       return count;
   }
   public static void main(String[] args)
   {
       String str = "malayalam";
       char x = 'a';
       int count = Frequency(str, x);
       System.out.print("The frequency of the character '" + x + "' in the string '"+str+"' = " + count);
   }
}
```
