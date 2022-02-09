#### Sorting Arrays

Starting with an unordered array of elements and rearranging them into nondecreasing order

##### The Insertion-Sort Algorithm

Algorithm InsertionSort(A):

​	Input: An array *A* of *n* comparable elements

​	Output: The array *A* with elements rearranged in non decreasing order

​		**for** *k* form 1 to *n - 1* **do**

​				Insert *A[k]* at its proper location within *A[0]*, *A[1]*, …, *A[k]*.

```java
public static void insertionSort(char[] data){
	int n = data.length;
	for (int k = 1; k < n; k++){
	char cur = data[k];
	int j = k;
	while (j > 0 && data[j-1] > cur){
		data[j] = data[j-1];
		j--;
		}
	data[j] = cur;
	}
}
```



![image-20210620120134289](image-20210620120134289.png)





#### Singly Linked Lists

###### To reverse a Linked Lists

[Recursion和Stack方法](https://www.geeksforgeeks.org/reverse-a-linked-list/)

```java
// Java program for reversing the linked list

class LinkedList {

	static Node head;

	static class Node {

		int data;
		Node next;

		Node(int d)
		{
			data = d;
			next = null;
		}
	}

	/* Function to reverse the linked list */
	Node reverse(Node node)
	{
		Node prev = null;
		Node current = node;
		Node next = null;
		while (current != null) {
			next = current.next;
			current.next = prev;
			prev = current;
			current = next;
		}
		node = prev;
		return node;
	}

	// prints content of double linked list
	void printList(Node node)
	{
		while (node != null) {
			System.out.print(node.data + " ");
			node = node.next;
		}
	}

	// Driver Code
	public static void main(String[] args)
	{
		LinkedList list = new LinkedList();
		list.head = new Node(85);
		list.head.next = new Node(15);
		list.head.next.next = new Node(4);
		list.head.next.next.next = new Node(20);

		System.out.println("Given Linked list");
		list.printList(head);
		head = list.reverse(head);
		System.out.println("");
		System.out.println("Reversed linked list ");
		list.printList(head);
	}
}

// This code has been contributed by Mayank Jaiswal

```

![img](RGIF2.gif)

###### Dummy Node

A dummy node at the front/end of the list that is there only to reduce the need for special-case code in the linked-list operations. It is an empty template to build new nodes later. 

要对头结点进行操作时，考虑创建哑节点dummy，使用dummy->next表示真正的头节点。这样可以避免处理头节点为空的边界问题。

###### 快慢指针 Hare tortoise

所谓快慢指针中的快慢指的是指针向前移动的步长， 每次移动的步长较大即为快，步长较小即为慢。 应用： 找到位置长度单链表中间节点。判断单链表是否有环（循环链表）

#### Circularly Linked Lists

#### Doubly Linked Lists

#### The List ADT

Java defines a general interface, `java.util.List`, that includes the following index-based methods:

![image-20210620120942049](image-20210620120942049.png)

![image-20210620121137868](image-20210620121137868.png)

```java
public interface List<E> { 
   	int size( );
    boolean isEmpty( );

 E get(int i) throws IndexOutOfBoundsException;


 E set(int i, E e) throws IndexOutOfBoundsException;

 void add(int i, E e) throws IndexOutOfBoundsException;


 E remove(int i) throws IndexOutOfBoundsException;
 }
```



#### Array Lists

An obvious choice for implementing the list ADT is to use an array A, where A[i] stores a reference to the element with index i. 

```java
public class ArrayList<E> implements List<E> { 
    // instance variables
 public static final int CAPACITY=16; 
    // default array capacity
 private E[ ] data; // generic array used for storage
 private int size = 0; // current number of elements
 // constructors
 public ArrayList( ) { this(CAPACITY); } // constructs list with default capacity
 public ArrayList(int capacity) { // constructs list with given capacity
 data = (E[ ]) new Object[capacity]; // safe cast; compiler may give warning
     
     public int size() {
	return size;
}
@Override
public boolean isEmpty() {
	return size == 0;
}
@Override
public E get(int i) throws IndexOutOfBoundsException {
	checkIndex(i, size);
	return data[i];
}
@Override
public E set(int i, E e) throws IndexOutOfBoundsException {
	checkIndex(i, size);
	 E temp = data[i];
	 data[i] = e;
	 return temp;
}
@Override
public void add(int i, E e) throws IndexOutOfBoundsException {
	checkIndex(i, size + 1);
	 if (size == data.length) // not enough capacity
	 throw new IllegalStateException("Array is full");
	 for (int k = size-1; k>=i;k--)
	 data[k+1] = data[k];
	 data[i] = e; // ready to place the new element
	  size++;
}
@Override
public E remove(int i) throws IndexOutOfBoundsException {
	checkIndex(i, size);
	 E temp = data[i];
	 for (int k = i; k <size-1; k++)
		 data[k] = data[k+1];
	 data[size-1] = null;
	 size--;
	 return temp;
}
protected void checkIndex(int i, int n) throws IndexOutOfBoundsException {
 if (i < 0 || i >= n)
 throw new IndexOutOfBoundsException("Illegal index: " + i);
 }
 }
```

##### Dynamic Array

made possible no limitation



when a call to add a new element risks ***overflowing*** the current array, we perform the following additional steps:

1. allocate a new array N with larger capacity
2. set B[k] = A[k], for k = 0,… ,n-1, where n denotes current number of items
3. Set A = B, what is, we henceforth use the new array to support the list
4. Insert the new element in the new array

```java
/∗∗ Resizes internal array to have given capacity >= size. ∗/
protected void resize(int capacity) {
E[ ] temp = (E[ ]) new Object[capacity]; // safe cast; compiler may give warning
for (int k=0; k < size; k++)
	temp[k] = data[k];
data = temp; // start using the new array
    //more following
}
```

A commonly used rule is for the new array to have twice the capacity of the existing array

that has been filled.

#### Positional Lists

#### Iterators

An ***iterator*** is a software design pattern that abstracts the process through a sequence of elements, one element at a time 

**迭代器模式**是一种行为设计模式， 让你能在不暴露集合底层表现形式 （列表List、 栈Stack和树Tree等） 的情况下遍历集合中所有的元素。

https://refactoringguru.cn/design-patterns/iterator

