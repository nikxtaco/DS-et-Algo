# Doubly Linked List

### Q. Write a Java program for the following: Create a doubly linked list of elements, delete a given element from the list, and display the contents of the list after deletion.
```
import java.io.*;

class Main
{
  List start;

  class List
  {
    int value;
    List next;
    List prev;
    List(int data)
    {
      value = data;
    }
  }

  void insert(int element)
  {
    List newnode = new List(element);
    newnode.next = null;
    List temp = start;

    if(start == null)
    {
      newnode.prev = null;
      start = newnode;
      return;
    }

    while(temp.next != null)
    {
      temp = temp.next;
    }

    temp.next = newnode;
    newnode.prev = temp;
  }

  int delete(int element)
  {
    List temp = start;

    if(temp.value == element)
    {
      if(temp.next == null)
      { 
        start = null;
        return 1;
      }
      else
      {
        start = start.next;
        start.prev = null;
        return 1;
      }
    }

    while(temp != null && temp.value != element)
    {
      temp = temp.next;
    }
    if(temp != null && temp.value == element)
    {
      temp.prev.next = temp.next;
      temp.next.prev = temp.prev;
      temp = null;
      return 1;
    }
    else
      return 0;
  }

  void display()
  {
    List node = start;
    System.out.print("The elements in the list are: ");
    while(node != null)
    {
      System.out.print(node.value + "  ");
      node = node.next;
    }
    System.out.println();
  }

  public static void main(String args[]) throws IOException
  {
    Main d1 = new Main();
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

    System.out.print("Enter the first element of the list: ");
    int x,res;
    char ch;
    x = Integer.parseInt(br.readLine());
    d1.insert(x);
    System.out.println("Element inserted successfully");

    do 
    {
      System.out.print("Would you like to add another node to the list(Y/N):  ");
      ch = br.readLine().charAt(0);
      if(ch == 'y' || ch == 'Y')
      {
        System.out.print("Enter the next element of the list: ");
        x = Integer.parseInt(br.readLine());
        d1.insert(x);
        System.out.println("Element inserted successfully");  
      }
    }while(ch != 'n' && ch != 'N');

    System.out.print("\nEnter the element to be deleted: ");
    x = Integer.parseInt(br.readLine());
    res = d1.delete(x);

    if(res == 1)
      System.out.println("The node was deleted successfully");
    else
      System.out.println("There is no node with the value " + x + "; Deletion unsuccessful");

    d1.display();
  }
}
```
