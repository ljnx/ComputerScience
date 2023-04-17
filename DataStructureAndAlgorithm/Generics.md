# Generics
Why
	Benefits	
		Avoid casting in client
		Detect erros at compile-time
Usage
	Generic stack
		linked-list implementation
			```Java
			public class Stack<Item>
			{
			  private Node first = null;

			  private class Node
			  {
			    Item item;
			    Node next;
			  }

			  public boolean isEmpty()
			  {  return first == null;  }

			  public void push(Item item)
			  {
			    Node oldfirst = first;
			    first = new Node();
			    first.item = item;
			    first.netx = oldfirst;
			  }

			  public Item pop()
			  {
			    Item item = first.item;
			    first = first.next;
			    return item;
			  }
			}
			```
		array implementation
			```java
			public class FixedCapacityStack<Item>
			{
			  private Item[] s;
			  private int N = 0;

			  public FixedCapacityStack(int capacity)
			  // not allowd generic collection {  s = new Item[capacity];  }
			  // the ugly cast
			  {  s = (Item[]) new Object[capacity];  }
			  

			  public boolean isEmpty()
			  { return N == 0;  }

			  public void push(Item item)
			  {  s[N++] = item;  }

			  public Item pop()
			  {  return s[--N];  }
			  }
			  ```


