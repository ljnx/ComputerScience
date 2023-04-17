# Stack
Reference	[Stack](https://www.coursera.org/learn/algorithms-part1/lecture/jSxyD/stacks)
What	LIFO
Test Client
	Input	`1 2 -`
	Output	`2 1`
Implementation	
	Method1	Linked List
		Code 	
		```Java 
		public class LinkedStackOfStrings 
		{
			private Node first = null;

			private class Node
			{
				String item;
				Node next;
			}

			public boolean isEmpty()
			{	return first == null;	}

			public void push(String item)
			{
				Node oldfirst = first;
				first = new Node();
				first.item = item;
				first.next = oldfirst;
			}

			public String pop()
			{
				String item = first.item;
				first = first.next
				return item;
			}
		}
		```
		Performance
			Time	constant time in the worst case
			Memory	~40N bytes(not include item itself)
	Method2	Fixed array
		Code
		```Java
		public class FixedCapacityStackOfStrings
		{
			private String[] s;
			private int N=0;

			public FixedCapacityStackOfStrings(int capacity)
			{	s = new String[capacity];	}

			public boolean is Empty()
			{	return N == 0;	}

			public void push(String item)
			{	s[N++] = item;	}
			
			// doesn't this code pop the second to last item?
			pubilc String pop()
			{	String item = s[--N];
				s[N] = null;
				return item;
			}
				
		}
		```

		Defect
			Stack overflows when n > capacity
			Underflow: throw exception if pop from an empty stack
	Method3 Resizing array
		Code
		```Java
		public class ResizingArrayStackOfStrings
		{
			private String[] s;
			private int N=0;
			
			public ResizingArrayStackOfStrings()
			{	s = new String[1];	}
			
			public void push(String item)
			{
				if (N == s.length) resize(2 * s.length);
				s[N++] = item;
			}

			public void resize(int capacity)
			{
				String[] copy = new String[capacity];
				for(int i  = 0; i < N; i++)
					copy[i] = s[i];
				s = copy;
			}

			public String pop()
			{
				String item = s[--N];
				s[N] = null;
				if (N > 0 && N = s.length/4) resize(s.length/2);
				return item;
			}
		}
		```

		Performance
			Time	N in the worst case


