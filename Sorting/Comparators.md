## Comparator

## x.compareTo(y)
- --> x < y
+ --> x > y
0 --> x == y 

## insertionSort with Strings

```java
public void insertionSort(String[] array) {
	for(int i=1; i<array.length; i++) {
		for(int k=i; k>0 && array[k-1].compareTo(array[k]) > 0; k++) {
			swap(array, k, k-1);
		}
	}
}
```

## compareTo Strings
```java
public int compareTo(String s) {
	for(int i=0; i<this.length() && i<s.length(); i++) {
		if(this.charAt(i) < s.charAt(i))
			return -1
		else if(this.charAt(i) < s.charAt(i))
			return 1
	}
	return this.length() - s.length();
}
```