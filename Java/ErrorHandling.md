# Error Handling

## Q1. Write a Java program that shows the usage of try, catch, throws and finally.
```
public class Main
{
    public static void main(String args[]) throws ArrayIndexOutOfBoundsException
    {
        try
        {
            int a[] = new int[6];
            System.out.println("Accessing element 7: " + a[7]);
        }
        catch (ArrayIndexOutOfBoundsException e)
        {
            System.out.println("Exception thrown: " + e);
        }
        finally
        {
            System.out.println("Finally has been performed.");
        }
    }
}
```
## Q2. Write a Java program that shows the usage of try, catch, throws and finally. Write a java program to read a set of strings from the keyboard and display the sorted strings in ascending order. (String input can be stopped by entering "end" as the last string). Perform sorting independent of case of letters.
```
import java.io.*;
 
class Main
{
   public static void main(String args[])throws IOException
   {
       String s1="end";
       String s[] = new String[20];
       int j=0,k;
 
       System.out.println("Enter a string ending with 'end':");
       BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
 
       for(int i=0;i<100;i++)
       {
           s[i] = br.readLine();
           j++;
           if(s[i].equals(s1))
           break;
       }
       for(i=0;i<j-1;i++)
         for(k=i+1;k<j-1;k++)
         {
             if(s[k].compareTo(s[i])<0)
             {
               String t=s[i];
               s[i]=s[k];
               s[k]=t;
             }
         }
        
       System.out.println("\nThe sorted string is: ");
       for(i=0;i<j-1;i++)
       {
           System.out.print(s[i]+" ");
       }
   }
}
```
## Q3. Write a java program to read a line of text and a word from the keyboard and search that word in the line of text. Index positions of all occurrences of the word should be printed as output. If no matching was found, that should be reported.
```
import java.io.*;
 
class Main
{
   public static void main(String args[])throws IOException
   {
       String s1;
       String s;
       int t,i;
       int flag=1;
 
       BufferedReader br = new BufferedReader (new InputStreamReader(System.in));
 
       System.out.println("Enter your string:");
       s=br.readLine();
 
       System.out.println("Enter the substring to be searched:");
 
       s1=br.readLine();
       t=0; i=0;
       s=s+' ';
       s1=s1+' ';
 
       do
       {
           if(s.indexOf(s1,t)!=-1)
           {
             t=s.indexOf(s1,t);
             System.out.println(t);
             flag=0;
             t=t+s1.length();
             i=t;
           }
           else
             i++;
       }
 
       while(i<s.length());
       if(flag==1)
        System.out.println("Substring is not found.");
   }
}
```
## Q4. Write a file handling program in Java with reader/writer. 
```
import java.io.*;
 
class Main
{
    public static void main(String args[]) throws IOException
    {
        char x;
        int i;
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        FileWriter fout = new FileWriter("output.txt");
        System.out.println("Enter the string: ");

        String str = br.readLine();
        try
        {
            for(i=0;i<str.length();i++)
            {
                x=str.charAt(i);
                fout.write((int)x);
            }
        }
        catch(IOException e)
        {
            System.out.println("error in writing file");
        }
        fout.close();
        FileReader fin = new FileReader("output.txt");

        try
        {
            do
            {
                i = fin.read();
                if(i != -1)
                System.out.println((char) i);
            }while(i != -1);
        }

        catch(IOException e)
        {
            System.out.println("Error in writing file.");
        }
        fin.close();
    }
}
```
## Q5. Write a Java program that read from a file and write to file by handling all file related exceptions.
```
import java.io.*;

public class Main
{
    public static void main(String args[]) throws IOException
    {
    int x;
    FileReader fin = null;
    FileWriter fout = null;
    try
    {
        fin = new FileReader("output.txt");
        fout = new FileWriter("copy.txt");
    }
    catch (IOException e)
    {
        System.out.println("Cannot read the file...");
    }

    try
    {
        System.out.println("Content of file output.txt:");
        do
        {  
            x = fin.read();
            if(x != -1)
            { 
                fout.write((char)x);
                System.out.print((char)x);
            }
        }while(x != -1);
    }
    catch(IOException e)
    {
        System.out.println("Error in reading file or writting file...");
    }
    fin.close();
    fout.close();
    FileReader fcr = null;

    try
    {
        fcr = new FileReader("copy.txt");
    }
    catch (IOException e)
    {
        System.out.println("Cannot read the file...");
    }

    try
    {
        System.out.println("\nContent of file copy.txt:");
        do
        { 
            x = fcr.read();
            if(x != -1)
            {  
                System.out.print((char)x);
            }
        }while(x != -1);
    }
    catch(IOException e)
    {
        System.out.println("Error in reading file...");
    }
    fcr.close();
   }
}
```
