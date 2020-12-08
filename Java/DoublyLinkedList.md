# Doubly Linked List

### Q. Write a Java program for the following: Create a doubly linked list of elements, delete a given element from the list, and display the contents of the list after deletion.
```
import java.io.*;

class Main
{
  List beg;
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
    List temp = beg;

    if(beg==null)
    {
      newnode.prev = null;
      beg = newnode;
      return;
    }

    while(temp.next!=null)
    {
      temp = temp.next;
    }

    temp.next = newnode;
    newnode.prev = temp;
  }

  int delete(int element)
  {
    List temp = beg;

    if(temp.value==element)
    {
      if(temp.next==null)
      { 
        beg = null;
      }
      else
      {
        beg = beg.next;
        beg.prev = null;
      }
      return 1;
    }

    while(temp!=null && temp.value!=element)
    {
      temp = temp.next;
    }
    if(temp!=null && temp.value==element)
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
    List node = beg;
    System.out.print("\nThe list is as follows: \n");
    while(node!=null)
    {
      System.out.print(node.value + "  ");
      node = node.next;
    }
    System.out.println();
  }

  public static void main(String args[]) throws IOException
  {
    Main dll = new Main();
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

    System.out.print("\nEnter an element into the list: ");
    int x,res;
    char ch;
    x = Integer.parseInt(br.readLine());
    dll.insert(x);
    System.out.println("Done.");

    do 
    {
      System.out.print("Do you want to add another node to the list? Press Y if yes:  ");
      ch = br.readLine().charAt(0);
      if(ch == 'y' || ch == 'Y')
      {
        System.out.print("Enter the next element: ");
        x = Integer.parseInt(br.readLine());
        dll.insert(x);
        System.out.println("Done.");  
      }
    }while(ch == 'y' || ch == 'Y');

    System.out.print("\nEnter the element to delete: ");
    x = Integer.parseInt(br.readLine());
    res = dll.delete(x);

    if(res==1)
      System.out.println("Done.");
    else
      System.out.println("There is no node with the value " + x + ".");
    dll.display();
  }
}
```
