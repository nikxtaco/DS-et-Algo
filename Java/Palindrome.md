# Palindrome

#### Q. Check whether a given string is a palindrome or not. Ex: MALAYALAM is a palindrome.
```
public class Main 
{
   static boolean Palindrome(String str)
   {
       int i = 0, j = str.length() - 1;
        while (i < j) 
        {
           if (str.charAt(i) != str.charAt(j))
               return false;
           i++;
           j--;
        }
       return true;
   }
   public static void main(String[] args)
   {
       String str = "malayalam";
       if (Palindrome(str))
           System.out.print("The word '"+str+"' is a palindrome.");
       else
           System.out.print("The word '"+str+"' is not a palindrome.");
   }
}
```
