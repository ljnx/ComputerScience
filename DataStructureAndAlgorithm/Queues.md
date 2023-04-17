# Queues
Reference	[Queues](https://www.coursera.org/learn/algorithms-part1/lecture/5vgrm/queues)
What	FIFO	
API
	```Java
	public class QueueOfString
		// create an empty queue
		QueueOfStrings()

		//insert a new string onto queue
		void enqueue(String item)

		//remove and return the string
		String dequeue()

		//is the queue empty
		bollean isEmpty()
	```
Implementation
	Linked-list
		```Java
		public class LinkedQueueOfStrings
		{
			private Node first, last;
			
			pritvate class Node
			{	/* same as in StackOfStrings * / 	}

			public boolean isEmpty()
			{	return first == null;	}

			public void enqueue(String item)
			{
				Node oldlast = last;
				last  = new Node();
				last.item = item;
				last.next = null;
				if (isEmpty()) first = last;
				else	       oldlast.next = last;
			}

			public String dequeue()
			{
				String item = first.item;
				first = first.next;
				if (isEmpty()) last = null;
				return item;
			}
		}
		```
	Resizing array implementation
		
Client Test
