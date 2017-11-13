# Algorithms
### 10.10
---
When we sort we need a swap method:

Arrays do not have extra space, so to rearrange an array we cannot just create new stuff.

```java
private void swap(int[] arr, int p1, int p2) {
	int temp = arr[p1];
	arr[p1] = p2;
	arr[p2] = temp;
}
```

## Bubble Sort

This algorithm is pretty shitty but its easy to understand.

> [43, 1, 2, 0, 45, 4, 42]

We compare [0] and [1], and swap them if [0] > [1]
43 > 1, so we swap them.

Then we compare [1] and [2], and swap.
43 > 2, so swap

43 > 0, so swap.

43 not > 45, so we do not swap.

> [1, 2, 0, 43, 45, 4, 42]

Then we painfully do this for each num.

> [1, 0, 2, 43, 45, 4, 42]
> [0, 1, 2, 43, 45, 4, 42]
> [0, 1, 2, 4, 43, 45, 42]
> [0, 1, 2, 4, 43, 45, 42]


Verifying something is sorted is O(n). 

Any sorting algorithm we write will never run faster than O(n)

```java
public void bubbleSort(int[] array) {
	boolean done = false;
	while(!done) {
		done = true;
		for(int i=0; i<array.length-1; i++) {
			if(array[i] > array[i+1]) {
				done = false;
				swap(array, i, i+1);
			}
		}
	}
}
```
#### Big O(n^2)

[43, 1, 2, 0, 45]
done T
[1, 43, 2, 0, 45]
[1, 2, 43, 0, 45]
[1, 2, 0, 43, 45]
done F
[1, 0, 2, 43, 45]



## Think if we have an array in reverse order
[5 4 3 2 1]
[4 5 3 2 1]
[4 3 5 2 1]
[4 3 2 5 1]
[4 3 2 1 5]
---
[3 4 2 1 5]
[3 2 4 1 5]
[3 2 1 4 5]
---
[3 4 2 1 5]
[3 2 4 1 5]
[3 2 1 4 5]
.....

This algorithm is pretty titties. We even have to do an extra loop through the array to ensure it is sorted even after its sorted. 

The worst one ever.

Only one worse is bogo sort.

```java
// bogo sort
while(!arraySorted(array)) {
	shuffle(array)
}
```

## Selection Sort
[47 6  4  12 19]
[4  6  47 12 19]
[4  6  47 12 19]
[4  6  12 47 19]
[4  6  12 19 47]

### Takes only n swaps
You would use this if the swap is expensive. His example was if you are at amazon and the swap function moves robots around.

```java
public void selectionSort(int[] array) {
	for(int i=0; i<array.length-1; i++) {
		int smallest = i; // we store the indicies instead of the value
		for(int k=i+1; k<array.length; k++) {
			if(array[k] < array[smallest]) {
				smallest = k;
			}
		}
		swap(array, i, smallest)
	}
}
```
#### Big O(n^2)

But its a better O(n^2).
The problem is if you give it a sorted array, it will still take O(n^2) time.

## Insertion sort
Google this I am not typing this shit out.

```java
public void insertionSort(int[] array) {
	for(int i = 1; i < array.length; i++) {
		int k = i - 1;
		while(k > 1 && array[k-1] > array[k]) {
			swap(array, k, k-1);
			k--;			
		}
	}
}
```

#### Big O(n^2)
But is a better O(n^2), because it does less looping.
[0, 1, 2, 3, 4] will be O(n) because it wont loop the second time
[0, 8, 2, 3, 4] will be O(n) because it wont loop the second time

If the array is reverse, or the elements are just far from where they are, it does a lot of work.

Insertion sort is O(n) for near sorted array.

Time it takes to operate is proportional to how sorted it is

## Shell Sort
Insertion sort that we apply to subset of array based on gaps.

Insertion sort is shell sort with gap of 1.

[19	15	12	10	8	7	6	5	4	3	2	1]
use a gap of size 5
[*	15	12	10	8	*	6	5	4	3	*	1]
[2	15	12	10	8	7	6	5	4	3	19	1]
use a gap os size 3
[2	15	12	10	8	7	6	5	4	3	19	1]

Can't really do this with a linked list because you need to jump to beginning of array.

Does not really make sense to do this with small arrays.
#### Big O(n^1.5)


# Why do we sort?
1. Search
2. You know where min and max are. But also the second max.

#### Priority Queue
We gone talk ab this later. But it takes off the highest priorty.


## Binary Search
One of the most efficient jawns.
[5	8	13	14	19	22	29	50	51	56	61	80]
SEARCH FOR 42
(0, 11) Look at [6]
(6, 11) Look at [8]
(6, 7) Look at [>6] 
(7, 7)

#### O(log n)
in CS log's are default base 2.

### 10.11
---
```java
public int binarySearch(int[] arr, int toFind) {
	return binarySearch(arr, 0, array.length-1, toFind);
}

private int binarySearch(int[] arr, int start, int end, int toFind) {
	int mid = (start + end)/2
	if(arr[mid] == toFind)
		return mid
	else if(arr[mid] > toFind)
		return binarySearch(arr, mid+1, end, toFind)
	else
		return binarySearch(arr, start, mid-1, toFind)
}
```
