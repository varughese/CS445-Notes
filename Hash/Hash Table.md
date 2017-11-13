# Hash Table 
### 10.18

- Repeatable (Identity)
x.equals(y) => x.hashCode() == y.hashCode()
- Reasonably Quick
- Unique (sort of)

Has to be well distributed
In Java they are (int)

Sometimes Irreversible

## Ex
#### Integer --> intvalue
#### Long --> hm


## Strings
Length: "A" = "B"
Sum(Char values): "ABC" = "CBA"

(((A * 31 + B ) * 31) + C) * 31
31 is 1111 in Binary, and this will affect the low bits.


```java
public int hashCode() {
	if(hashcode == Integer.MAX_VALUE) {
		// hashcode hasnt been cached yet
		for(int i=0; i<this.length(); i++) {
			hashcode *= 31;
			hashcode += this.charAt(i);
		}
	}

	return hashcode;
}
```

### Hashing
Rectangle : x,y,w,h
### Stringification
`(x + "_" + y + "_" + w + "_" + h)(hashCode())`

# Hash Table
HashCode ==> % Array Length ==> Somewhere in Hash Table
(The address is dependent on the number of elements in the array)

## Linear Probing
Collision strategy. You put an element in and increment it.
When you delete something you have to push them all back.

Load Factor (λ) 0.5, then lookup becomes O(n)

Initiliaze Properly.
ArrayList with 17 things in it? Make it 17
Hash Table with 22 things? Make it 45 (for load factors)


## Separate Chaining
Keep chain sorted
Takes more memory, 8 bytes overhead.