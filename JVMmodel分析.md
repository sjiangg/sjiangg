

#### JVM

JVM is the one that calls the main method present in a java code. JVM is a part of JRE(Java Runtime Environment).

A programmer can develop Java code on one system and can expect it to run an any other Java-enabled system without any adjustment. This is all possible because of JVM



###### JVM  Memory

1. **Method area:** In the method area, all class level information like class name, immediate parent class name, methods and variables information etc. are stored, including static variables. There is only one method area per JVM, and it is a shared resource.

   

2. **Heap area:** Information of all objects is stored in the heap area. There is also one Heap Area per JVM. It is also a shared resource.

   

3. **Stack area:** For every thread, JVM creates one run-time stack which is stored here. Every block of this stack is called activation record/stack frame which stores methods calls. All local variables of that method are stored in their corresponding frame. After a thread terminates, its run-time stack will be destroyed by JVM. It is not a shared resource.

   

4. **PC Registers:** Store address of current execution instruction of a thread. Obviously, each thread has separate PC Registers.

   

5. **Native method stacks:** For every thread, a separate native stack is created. It stores native method information. 



![How JVM Works - JVM Architecture? - GeeksforGeeks](jvm-3.jpg)

![image-20210611183335067](image-20210611183335067.png)

##### Class Loader Subsystem

It is mainly responsible for 3 activities:

+ Loading

+ Linking 

+ Initializing

  

**Loading**:

The Class loader reads the *“.class”* file, generate the corresponding binary data and save it in the method area



####  Memory Hierarchies and Caching

With the increased use of computing in society, software applications must manage extremely large data sets. Such application include the processing of online financial transactions, the organization and maintenance of databases, and analyses of customers’ purchasing histories and preferences. The amount of data can be so large that the overall performance of algorithms and data structures sometimes depends more on the time to <u>access the data</u> than on the speed of the CPU

###### Memory Systems

In order to accommodate large data sets, computers have a hierarchy of different kinds of memories, which vary in terms of their size and distance from the CPU. Closest tot the CPU are the **internal registers that the CPU itself uses**. Access to such locations is very fast, but there are relatively few such locations. 

At the second level in the hierarchy are one or more memory **caches**. This memory is considerably larger than the register set of a CPU, but accessing it takes longer. 

At the third level in the hierarchy is the **internal memory**, which is also known as **main memory ** or **core memory**. The internal memory is considerably larger than the cache memory, but also requires more time to access.

Another level in the hierarchy is the **external memory**, which usually consists of disks, CD drives. This memory is very large, but it is also very slow. Data stored through an external network can be viewed as yet another level in this hierarchy, with even greater storage capacity, but even slower access.

Thus, the memory hierarchy for computers can be viewed as consisting of *five or more levels,* each of which is larger and slower than the previous level.

![image-20210613204742872](image-20210613204742872.png)

##### Caching Strategies

The significance of the memory hierarchy on the performance of a program depends greatly upon the size of the problem we are trying to solve and the physical characteristics of the computer system. 

For a problem that can fit entirely in main memory, the two most important levels are the cache memory and the internal memory. Access times for internal memory can be as much as 10 to 100 times longer than those for cache memory.

It is desirable, therefore, to be able to perform most memory accesses in cache memory. It is desirable to be able to perform most memory accesses in <u>cache memory.</u>

For a problem that does not fit entirely in main memory, on the other hand, the two most important levels are the <u>internal memory</u> and the <u>external memory</u>. 

 

###### Caching and Blocking

Operating system designers have developed general mechanisms that allow most memory accesses to be fast. These mechanisms are based on two important **locality-of-reference** properties that most software possesses:

+ Temporal locality:	

  + If a program accesses a certain memory location, then there is increased likelihood that it accesses that <u>same location again</u> in the near future. For example,

    时间局限性: 被引用过一次的存储器位置在未来会被多次引用

+ Spatial locality

  + If a program accesses a certain memory location, then there is increased likelihood that it soon accesses <u>other locations</u> that are near this one. 

    空间局限性: 如果一个存储器的位置被引用, 那么将来它附近的位置也会被引用

```java
int a[N] = {2, 3, 4};
int sum = 0;
for (int i = 1; i <N; i++){
		sum = sum + a[i];}
```

在上述代码中, 

1. sum 为temporal locality, 因为sum被引用了很多次
2. 数组元素为spatial locality, 因为如果a[i]被引用, 则a[i+1]…很可能被引用



The two localities have given rise to 2 fundamental design choices for multilevel computer memory systems

1. **virtual memory**
   - This concept consists of providing an address space as large as the capacity of the secondary-level memory, and of transferring data located in the secondary level into the primary level, when they are addressed. 
   - Virtual memory does not limit the programmer to the constraint of the internal memory size.
   - The concept of bringing data into primary memory is called ***caching***, and it is motivated by temporal locality.
2. **blocking**
   - If data stored at a secondary-level memory location *l* is accessed, then we bring into primary-level memory a large block of contiguous locations that include the location *l*.
   - In the interface between cache memory and internal memory, such blocks are often called **cache lines**, and in the interface between internal memory and external memory, such blocks are often called **pages**.

###### Page Replacement Algorithms

- Random
- FIFO
- LRU

