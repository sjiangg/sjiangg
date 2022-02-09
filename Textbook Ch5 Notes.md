### Textbook Ch5 Notes 

###### 			Recursion



1. The **Factorial function** (commonly denoted as n!) is a classic mathematical function that has a natural recursive definition.

   

2. An **English ruler** has a recursive pattern that is a simple example of a fractal structure. 

   

3. **Binary search ** is among the most important computer algorithms. It allows us to efficiently locate a desired value in a data set with upwards of billions of entries. 

   

4. The **file system ** for a computer has a recursive structure in which directories can be nested arbitrarily deeply within other directories. Recursive algorithms are widely used to explore and manage these file systems. 



--------------------------------------



#### The Factorial Function 

The factorial of a positive integer n, denoted n!, is defined as the product of the integers from 1 to n. If n = 0, then n! is defined as 1.

 ![](ch5_Fac.png)

​				For example, 5! = 5 * 432*1 = 120. 

Factorial is known to equal the number of ways in which n distinct items can be arranged into a sequence, that is, the number of **permutations** of n items. 

for example, 5 items can be arranged in 120 ways. we see 5! = 5 * 4!. We can define n! to be n(n-1)!. This recursive definition can be formalized as ![](ch5_fac1.png) 

```java
  public static int factorial(int n) throws IllegalArgumentException {  
  	if (n < 0) throw new IllegalArgumentException( );  	
   		 // argument must be nonnegative 	
    else if (n == 0) 		
    	return 1; 
    	// base case  
    else return n ∗ factorial(n - 1); 
    	// recursive case }
```





A total number of n+1 activations. the over-all number of operations for computing **factorial(n)** is O(n) 

#### Drawing an English Ruler



```java
//∗ Draws an English ruler for the given number of inches and major tick length. 
    public static void drawRuler(int nInches, int majorLength) { 
    drawLine(majorLength, 0);
    // draw inch 0 line and label  
    for (int j = 1; j <= nInches; j++) { 	
        drawInterval(majorLength - 1);   // draw interior ticks for inch 	 		
        drawLine(majorLength, j);   // draw inch j line and label 
    }   
} 

private static void drawInterval(int centralLength) { 
    if (centralLength >= 1) { // otherwise, do nothing  
        drawInterval(centralLength h 1); // recursively draw top interval  
        drawLine(centralLength); // draw center tick line (without label)  
        drawInterval(centralLength h 1); // recursively draw bottom interval   
    }  }  

private static void drawLine(int tickLength, int tickLabel) { 
    for (int j = 0; j < tickLength; j++) 	 
        System.out.print("-"); 
    if (tickLabel >= 0) 	 System.out.print(" " + tickLabel);  
    System.out.print("\n");
} // Draws a line with the given tick length (but no label). ∗/
   
    private static void drawLine(int tickLength) { 
    drawLine(tickLength, , 1); 
}
```

O(2^n)  





#### Binary Search



 used to efficiently locate a target value within a sorted sequence of n elements stored in an array. when the sequence is **unsorted**, we use a loop to examine every element. This algorithm is known as **linear search** , runs in O(n) time. Binary Search runs in O(log n ) time. 

``` java
//Returns true if the target value is found in the indicated portion of the data array.  
//∗ This search only considers the array portion from data[low] to data[high] inclusive. ∗/  
    public static boolean binarySearch(int[ ] data, int target, int low, int high) {
    	if (low > high) 	 
            return false; // interval empty; no match 
    else { 	int mid = (low + high) / 2; 
          if (target == data[mid]) 	 
              return true; // found a match else if (target < data[mid]) 	
          return binarySearch(data, target, low, mid - 1);  	 // recur left of the middle 
          else 	 	
              return binarySearch(data, target, mid + 1, high);  	 // recur right of the middle 
         } }
```

 O(log n )



#### File System 

Pseudocode: ![](cha5_fac2.png)



:smile:

`printf()`

~~wrong~~

✨✔👀😃🌹🌹

==highlight==



```java
//∗∗ ∗ Calculates the total disk usage (in bytes) of the portion of the file system rooted at the given path, while printing a summary akin to the standard 'du' Unix tool. ∗/
public static long diskUsage(File root) {
    long total = root.length( );  // start with direct disk usage 
    if (root.isDirectory( )) { // and if this is a directory, 	 
        for (String childname : root.list( )) {  	 // then for each child 		
            File child = new File(root, childname);  		 // compose full path to child 		
            total += diskUsage(child);  		 // add child’s usage to total 	 
        } 
    }  System.out.println(total + "\t" + root);   // descriptive output 
    return total; // return the grand total }
```

 O(n)



------------------------------------------- -

  * If a recursive call starts at most one other, we call it a **linear recursion** -
  * If a recursive call may start two others, we call it a **binary recursion** -	
  * If a recursive call may start three or more others, this is **multiple recursion**

### Linear Recursion

the implementation of the factorial method and binary search algorithm are clear examples of linear recursion. Examples: 

 /∗∗ Returns the sum of the first n integers of the given array. ∗/  public static int linearSum(int[ ] data, int n) { 	if (n == 0) 	 return 0; 	else 	 return linearSum(data, nn 1) + data[nn 1]; } 

```java
 // Returns the sum of the first n integers of the given array. ∗/
     public static int linearSum(int[ ] data, int n) { 
     if (n == 0) 	 return 0; 
     else 	
         return linearSum(data, nn 1) + data[nn 1];
   }
```





For an input of size n, the `linearSum` algorithm makes n+ 1 method calls. Hence, it will take O(n) time, because it spends a constant amount of time performing the non-recursive part of each call.  

Moreover, we can also see that the memory space used by the algorithm (in addition to the array) is also O(n)

```java
//∗∗ Reverses the contents of subarray data[low] through data[high] inclusive. ∗/  
public static void reverseArray(int[ ] data, int low, int high) { 	
    if (low < high) { // if at least two elements in subarray 	 
        int temp = data[low]; // swap data[low] and data[high] 	 
        data[low] = data[high]; 	
        data[high] = temp;  
        reverseArray(data, low + 1, highh 1); // recur on the rest 
    }   }
```

Because each call involves a constant amount of work, the entire process runs in O(n) time. 

```java
//∗ Computes the value of x raised to the nth power, for nonnegative integer n. ∗/  
public static double power(double x, int n) { 	
    if (n == 0) 	 
        return 1; 	
    else 	 
        return x ∗ power(x, n - 1); 
}
```

 A recursive call to this version of power(x,n) runs in O(n) time. 

A revised version: 

```java
//∗ Computes the value of x raised to the nth power, for nonnegative integer n. ∗/  
public static double power(double x, int n) { 	
    if (n == 0) 	 
        return 1; 	
    else { 		
        double partial = power(x, n/2);  		// rely on truncated division of n 		
        double result = partial ∗ partial; 		 
        if (n % 2 == 1)  		 // if n odd, include extra factor of x 		
            result ∗= x; 		
        return result; 
    } }
```



The improved version also provides significant saving in reducing the memory usage. The first version has a recursive depth of *O(n)*, and therefore, *O(n)* frames are simultaneously stored in memory.  Because the recursive depth of the improved version is *O(log n)*, its memory usage is *O(log n)* as well. ####



### Binary Recursion



 the implementation of English Ruler.  Write summing n integers of an array by binary recursion 

```java
// Returns the sum of subarray data[low] through data[high] inclusive. ∗/  
public static int binarySum(int[ ] data, int low, int high) { 
    if (low > high) // zero elements in subarray  	
        return 0; 
    else if (low == high) // one element in subarray 
        return data[low]; 
    else { 	int mid = (low + high) / 2; 	 
          return binarySum(data, low, mid) + binarySum(data, mid+1, high);
         }
}
```



The size of the range is divided in half at each recursive call, and so the depth of the recursion is 1+log2 n. Therefore, `binarySum` uses *O(log n)* amount of additional space, which is a big improvement over the *O(n)* space used by the `linearSum` method of Code Fragment 5.6.  However, the running time of `binarySum` is *O(n)*, as there are 2n - 1 method calls, each requiring constant time.

