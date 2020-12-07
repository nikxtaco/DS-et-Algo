# Read/Write

## Q1. Write a file handling program in Java with reader/writer. 
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
    ## Q2. Write a Java program that read from a file and write to file by handling all file related exceptions.
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