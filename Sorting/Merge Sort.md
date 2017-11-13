# Merge Sort

17 19 4 6 3 1 2 9

17 19 4 6 | 3 1 2 9

17 19 | 4 6 | 3 1 | 2 9

17 | 19 | 4 | 6 | 3 | 1 | 2 | 9

17 19 | 4 6 | 1 3 | 2 9

4 6 17 19 | 1 2 3 9

1 2 3 4 6 9 17 19

# O(log n) and O(2n)
# O(n log n)

```java
public void mergeSort(int[] array, int[] temp) {
	mergeSort(array, temp, 0, array.length);
}

private void mergeSort(int[] array, int[] temp, start, end) {
	int mid = (start+end)/2;
	if(start != end) {
		mergeSort(array, temp, start, mid);
		mergeSort(array, temp, mid, end);
	}
	merge(array, temp, start, mid, end);
}

private void merge(int[] array, int[] temp, int start, int mid, int end) {
	int b1 = start;
	int b2 = mid;
	int index = 0;
	while(b1 < mid && b2 < end) {
		if(array[b1] <= array[b2]) {
			temp[index] = array[b1];
			b1++;
		} else {
			temp[index] = array[b2];
			b2++;
		}
		index++;
	}
	// if(b1 == mid) {
		while(b2 < end) {
			temp[index++] = array[b2++];
		}
	// } else {
		while(b1 < mid) {
			temp[index++] = array[b1++];
		}
	// }
	System.arraycopy(temp, 0, array, start, index);
}
```