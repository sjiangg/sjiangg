##### Stacks 



A ***\**\*\**stack\**\*\*\**** is a collection of objects that are inserted and removed according to the ***\**\*\**\*last in, first-out LIFO\**\*\*\***** principle. 

A user may insert objects into a stack at any time, but may only access or remove the most recently inserted object that remains( at the so-called "top" of the stack). 

- Stacks are a fundamental data structure. they are used in many applications:  - 
  - Internet Web Browsers store the addresses of recently visited sites on a stack. Each time a user visits a new site, that site's address is "'pushed '" onto the stack of addresses. The browser then allows the user to "pop" back to previously visited sites using the "back" button.  
  -  Text editors usually provide an “undo” mechanism that cancels recent editing operations and reverts to former states of a document. This undo operation can be accomplished by keeping text changes in a stack.  



###### The Stack ADT

Stacks are the simplest of all data structures, yet they are also among the most important, as they are used in a host of different applications, and as a tool for many more sophisticated data structures and algorithms. 

​		 update methods: 

​				![image-20210614175449216](image-20210614175449216.png)

​		accessor methods

​		![image-20210614175531293](image-20210614175531293.png)

###### A Stack Interface in Java

In order to formalize our abstraction of a stack, we define what is known as its ***application programming interface***(API) in the form of a Java **interface**, which describes the names of the methods that the ADT supports and how they are to be declared and used. 

```java
/∗∗
∗ A collection of objects that are inserted and removed according to the last-in
∗ first-out principle. Although similar in purpose, this interface differs from
∗ java.util.Stack.
∗/

public interface Stack<E> {
 /∗∗
∗ Returns the number of elements in the stack.
 ∗ @return number of elements in the stack
∗/
 int size( );

 /∗∗
 ∗ Tests whether the stack is empty.
 ∗ @return true if the stack is empty, false otherwise
 ∗/
 boolean isEmpty( );

 /∗∗
 ∗ Inserts an element at the top of the stack.
 ∗ @param e the element to be inserted
 ∗/
 void push(E e);

 /∗∗
 ∗ Returns, but does not remove, the element at the top of the stack.
 ∗ @return top element in the stack (or null if empty)
 ∗/
 E top( );

 /∗∗
 ∗ Removes and returns the top element from the stack.
 ∗ @return element removed (or null if empty)
 ∗/
 E pop( );
 }
```

—Interface Stack documented with comments in Javadoc style. Note the use of the generic parameterized type, E, which allows a stack to contain elements of any specified (reference) type.—

###### The `java.util.Stack` Class

Because of the importance of the stack ADT, Java has included a concrete class named `java.util.Stack` that implements the LIFO semantics of a stack. 

However, it is not recommended to be used

It is used for <u>double ended queue</u>

###### A simple array-based stack class:

```java
public class ArrayStack<E> implements Stack{
public static final int CAPACITY = 1000;
private E[] data;
private int t = -1;//index of the top element. also the size of stack
public ArrayStack() { this(CAPACITY);}
public ArrayStack(int capacity) {
	data = (E[]) new Object[capacity]; //safe cast
}
	@Override
	public void push(E e) throws IllegalStateException {
		if(size() == data.length) throw new IllegalStateException("Stack full");
		data[++t] = e;	
        //increment t before storing new item
	}
	@Override
	public boolean isEmpty() {
		return (t==-1);
	}
	@Override
	public int size() {
		return (t+1);
	}
	@Override
	public Object top() {
		if(isEmpty()) return null;
		return data[t];
	}
	@Override
	public Object pop() {
		if(isEmpty()) return null;
		E answer = data[t];
		data[t] = null;		
        //dereference to help gc
		t--;
		return answer;
	}


}

```

###### A drawback of this Array-Based Stack Implementation

The array implementation of a stack is simple and efficient. Nevertheless, this implementation has one negative effect: it relies on a fixed-capacity array, which limits the ultimate size of the stack. 

- we allow the user of a stack to specify the capacity as a parameter to the constructor. when a user knows the number of items needing to go in the stack, this implementation is perfect. But if the estimate is wrong, there can be grave consequences. If the application needs much less space than the reserved capacity, memory is wasted. 
  -  Worse yet, if an attempt is made to push an item onto a stack that has already reached its maximum capacity, the implementation throws an `IllegalStateException`
- therefore, we demonstrate 2 approaches for implementing a stack without such a size limitation and with space always proportional to the actual number of elements stored in the stack: 
  - ​	Singly linked list

#### Implementing a Stack with a Singly Linked List

😃👍🌹🌹🌹✨:-) 加油珊珊 你真棒

In this section, we demonstrate how the Stack interface can be easily implemented using a singly linked list for storage.



###### The Adapter Pattern

The ***adapter*** pattern applies to any context where we effectively want to modify an existing class so that its methods match those of a related, but different, class or interface. 

One general way to apply the adapter pattern is to define a new class which contains an instance of the existing class as a hidden field, and then to implement each method of the new class using methods of this hidden instance variable.

By applying the adapter pattern in this way, we have created anew class that performs some of the same functions as an existing class, but repackaged in a more convenient way. 

```java
public class LinkedStack<E> implements Stack<E> {
	private SinglyLinkedList<E> list = new SinglyLinkedList<>();//an empty list
	public LinkedStack() {}
	
	@Override
	public int size() {return list.size();}
	
	@Override
	public void push(E e) { list.addFirst(e);}

	@Override
	public boolean isEmpty() {	return list.isEmpty();}

	@Override
	public E top() { return list.first();}

	@Override
	public E pop() { return list.removeFirst();}

}
```

###### Reversing an array using a stack

As a consequence of the LIFO protocol, a stack can be used as a general toll to reverse a data sequence. For example, if the values 1,2,3 are pushed onto a stack in that order, they will be popped from the stack in the order 3, 2, 1. 

We create an empty stack for auxiliary storage, <u>push all of the array elements onto the stack,</u> and then <u>pop those elements off of the stack while overwriting the cells of the array from beginning to end.</u> 

```java
public  static<E> void reverse(E[] a) {
	Stack<E> buffer = new ArrayStack<>(a.length);
	//push elements in
	for(int i = 0; i<a.length;i++) {	
        buffer.push(a[i]);	}
	//then pop out and write in array
	for(int i = 0; i<a.length; i++) {
        a[i] = buffer.pop();	}
}

```

###### Matching Parentheses and HTML Tags

​	2 related applications of stacks both involve <u>testing for pairs</u> of <u>matching delimiters</u>. we use a stack to perform this task with a single left-to-right scan of the original string

​	

##### Queues

A queue is  a collection of objects that are inserted and removed according to the ***first-in, first-out (FIFO)***. FIFO queues are also used by many computing devices, such as a networked printer, or a Web server responding to requests.

###### The Queue ADT

The queue ADT defines a collection that keeps objects in a sequence, where <u>element access and deletion are restricted to the **first ** element in the queue,</u> and element <u>insertion in restricted to the **back** of the sequence</u>.

- update methods:

  ![image-20210618203258827](image-20210618203258827.png)

- access methods

![image-20210618203308297](image-20210618203308297.png)

###### A Queue Interface 

```java
public interface Queue<E> {
int size();
boolean isEmpty();
void enqueue(E e);
E first();
E dequeue();
}
```

###### The `java.util.Queue` Interface in Java

Java provides a type of queue interface, `java.util.Queue`, which has functionality similar to the traditional queue ADT, given above, but the documentation for the `java.util.Queue` interface does not insist that it support only the FIFO principle.



The `java.util.Queue` supports 2 styles for most operations, which vary in the way that they treat

###### Array-Base Queue Implementation

Use an array tot efficiently support the FIFO semantics of the Queue ADT.

Strategy 1: 

​			execute a loop to shift all other elements of the queue one cell to the left. This result in an *O(n)* running time for the `dequeue` method

Strategy 2: (no loop)

​			replace a dequeued element with a `null` reference, and maintain an explicit variable *f* to represent the index of the element that is currently at the front of the queue . This runs in *O(1)* time for `dequeue`.

###### 			Use an Array Circularly

​			![image-20210618215640057](image-20210618215640057.png)

​			The modulo operator is ideal for treating an array circularly.  we use the arithmetic *f* = (*f* +1) % *N* . 

​			For example: An array of length 10	

-  			front index 7: (7+1)%10 = 0 with a reminder of 8
  - ​		9: (9+1)%10 = 1 with a remainder of 0 (index at 0)

###### A Java Queue Implementation

```java
public class ArrayQueue<E> implements Queue<E> {
	public static final int CAPACITY = 1000;
	// instance variables
	 private E[ ] data; // generic array used for storage
	 private int f = 0; // index of the front element
	 private int sz = 0; // current number of elements
	 // constructors
	 public ArrayQueue( ) {this(CAPACITY);} // constructs queue with default capacity
	 public ArrayQueue(int capacity) { // constructs queue with given capacity
	 data = (E[ ]) new Object[capacity]; // safe cast; compiler may give warning
	 }
	
	// methods
	 //∗∗ Returns the number of elements in the queue. ∗/
	 public int size( ) { return sz; }
	
	 //∗∗ Tests whether the queue is empty. ∗/
	 public boolean isEmpty( ) { return (sz == 0); }
	
	 /**Inserts an element at the rear of the queue. */
	
	
	public void enqueue(E e) throws IllegalStateException {
	if (sz == data.length) throw new IllegalStateException("Queue is full");
	 int avail = (f + sz) % data.length; // use modular arithmetic
	 data[avail] = e;
	sz++;
	 }
	
	//∗∗ Returns, but does not remove, the first element of the queue (null if empty). ∗/
	
	
	public E first( ) {
	if (isEmpty( )) return null;
	 return data[f];
	 }
	
	 //∗∗ Removes and returns the first element of the queue (null if empty). ∗/
	 public E dequeue( ) {
	 if (isEmpty( )) return null;
	 E answer = data[f];
	data[f] = null; // dereference to help garbage collection
	f = (f + 1) % data.length;
	sz--;
	 return answer;
	 }
}
```

###### Implementing a Queue with a Singly Linked List

```java
public class LinkedQueue<E> implements Queue<E> {
	private SinglyLinkedList<E> list = new SinglyLinkedList<>( ); // an empty list

	public LinkedQueue( ) { } // new queue relies on the initially empty list
	public int size( ) { return list.size( ); } 
	public boolean isEmpty( ) { return list.isEmpty( ); }  
    public void enqueue(E element) {		 list.addLast(element); } 
	public E first( ) { return list.first( ); } 
	public E dequeue( ) { return list.removeFirst( ); }
 }
```

Each method of the class runs in *O(1)* worst-case time

A linked list uses more space per element than a properly sized array of references

###### A circular queue

```java
public interface CircularQueue<E> extends Queue<E> {
/∗∗
 ∗ Rotates the front element of the queue to the back of the queue.
 ∗ This does nothing if the queue is empty.
 ∗/ 
 void rotate( ); }
```

Solving Josephus problem with CircularQueue see code6.13





