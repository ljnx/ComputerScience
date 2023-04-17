# Iterators

Why
	Design Challenge
		Supports iteration over stack items by client, without revealing the internal representation of the stack
	Java Solution
		Make stack implements the `Iterable` interface

	
What
	`Iterable`	Has a method that returns an `Iterator`
	`Iterator`	Has methods `hasNext()` and `next()`
How
	Iterate over a `Iterable` data structures
		shorthand
			```java
			for (String s : stack)
				StdOut.println(s);
			```

		longhand
			```java
			Iterator<String> i = stack.iterator();
			while (i.hasNext())
			{
			  String s = i.next();
			  StdOut.println(s);
			}
			```

	Make data structures `Iterable`
		Stack iterator
			linked-list implementation
				```Java
				import java.util.Iterator

				public class Stack<Item> implements Iterable<Item>
				{
				  public Iterator<Item> iterator(){ return new ListIterator();  }

				  private class ListIterator implements Iterator<Item>
				  {
				    private Node current = first;

				    public boolean hasNext() {  return current != null;  }
				    public void remove()  { /* not surpported * }
				    public Item next()
				    {
				      Item item = current.item;
				      current = current.next;
				      return item;
				    }
				  }
				}
				```
			array implementation
				```Java
				import java.util.Iterator

				public class Stack<Item> implements Iterable<Item>
				{
				  public Iterator<Item> iterator()
				  {  return new ReverseAraryIterator();  }

				  public class ReverseArrayIterator implements Iterator<Item>
				  {
				     private int i = N;

				     public boolean hasNext(){  return i > 0;  }
				     public void remove(){ /* not supported */}
				     public Item next(){  return s[--i];  }
				  }
				}
				```
