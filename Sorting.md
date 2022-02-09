##### Insertion Sort

insertion sort is not a fast sorting algorithm because it uses nested loops to shift items into place. it is useful only for small data sets. it runs in O(n^2) time

```java
public static int[] insertionSort(int[] list) {
		int key, temp, j;
		for(int i = 1; i < list.length; i++) {
			j = i-1;
			key = list[i];
			while(j >= 0 && key < list[j]) {
				temp = list[j];
				list[j] = list[j+1];
				list[j+1] = temp;
				j--;
			}
		}
		return list;
	}
```

![image-20210703124620472](image-20210703124620472.png)

##### Merge Sort

Merge Sort is recursive, it is also a Divide-and-Conquer algorithm(breaking problem into smaller pieces). it is very efficient for large data sets. runs in O(n log n)

```java
public static void mergeSort (int[] list, int lowIndex, int highIndex) {
		if (lowIndex ==highIndex) return;
		else {
			int midIndex = (lowIndex + highIndex) /2;
			mergeSort(list, lowIndex, midIndex);
			mergeSort(list, midIndex + 1, highIndex);
			merge(list, lowIndex, midIndex, highIndex);
		}
	}
	
	 static void merge(int arr[], int l, int m, int r)
	    {
	        // Find sizes of two subarrays to be merged
	        int n1 = m - l + 1;
	        int n2 = r - m;
	 
	        /* Create temp arrays */
	        int L[] = new int[n1];
	        int R[] = new int[n2];
	 
	        /*Copy data to temp arrays*/
	        for (int i = 0; i < n1; ++i)
	            L[i] = arr[l + i];
	        for (int j = 0; j < n2; ++j)
	            R[j] = arr[m + 1 + j];
	 
	        /* Merge the temp arrays */
	 
	        // Initial indexes of first and second subarrays
	        int i = 0, j = 0;
	 
	        // Initial index of merged subarry array
	        int k = l;
	        while (i < n1 && j < n2) {
	            if (L[i] <= R[j]) {
	                arr[k] = L[i];
	                i++;
	            }
	            else {
	                arr[k] = R[j];
	                j++;
	            }
	            k++;
	        }
	 
	        /* Copy remaining elements of L[] if any */
	        while (i < n1) {
	            arr[k] = L[i];
	            i++;
	            k++;
	        }
	 
	        /* Copy remaining elements of R[] if any */
	        while (j < n2) {
	            arr[k] = R[j];
	            j++;
	            k++;
	        }
	    }
```



##### Quick Sort

recursive, it is also a Divide-and-Conquer algorithm(breaking problem into smaller pieces). it is very efficient for large data sets. 

Worst case O(n^2). Average case O(n log n). Performance depends largely on pivot selection



https://algorithm.yuanbin.me/zh-hans/basics_sorting/quick_sort.html

##### Selection Sort

核心：不断地选择剩余元素中的最小者。

```java
public static void selectionSort(int[] array) {
        int len = array.length;
        for (int i = 0; i < len; i++) {
            for (int item : array) {
                System.out.print(item + " ");
            }
            System.out.println();
            int min_index = i;
            for (int j = i + 1; j < len; j++) {
                if (array[j] < array[min_index]) {
                    min_index = j;
                }
            }
            int temp = array[min_index];
            array[min_index] = array[i];
            array[i] = temp;
        }
    }
```

##### Bubble Sort

核心：**冒泡**，持续比较相邻元素，大的挪到后面，因此大的会逐步往后挪，故称之为冒泡。

```java
 public static void bubbleSort(int[] nums) {
        int len = nums.length;
        for (int i = 0; i < len; i++) {
            for (int num : nums) {
                System.out.print(num + " ");
            }
            System.out.println();
            for (int j = 1; j < len - i; j++) {
                if (nums[j - 1] > nums[j]) {
                    int temp = nums[j - 1];
                    nums[j - 1] = nums[j];
                    nums[j] = temp;
                }
            }
        }
    }
```

#### divide-and-conquer

1. **Divide** 

   divide the input data into two or more disjoint subsets

2. **Conquer**

   Recursively solve the subproblems associated with the subsets

3. **Combine**

   take the solutions to the subproblems and merge them into a solution to the original problem
