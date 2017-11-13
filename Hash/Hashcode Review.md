What happens when we insert to a hash table to a key that exists: replace it

# Add with Linear Probing 
1. Hashcode
2. Address
3. Entry
4. Insert

```java
private void insertTable(Entry<K,V> entry, int address, int hashcode) {
	Entry<K,V> currentValue = table[address];
	if(currentValue == null) {
		table[address] = entry;
		size++;
	} else {
		if(entry.key.hashCode() < currentValue.key.hashCode()) {
			entry.next = currentValue;
			table[address] = entry;
			size++;
		} else {
			insertInChain(entry, currentValue, hashcode);
		}
	}
}

private void insertInChain(Entry<K,V> entry, Entry<K,V> current, int hashcode) {
	while(current.next != null && hashcode > current.next.key.hashCode()) {
		current = current.next;
	}
	if(current.next.hashCode() == hashcode) {
		if(entry.key.equals(current.next.key)) {
			entry.next = current.next.next;
			current.next = entry;
		} else {
			entry.next = current.next;
			current.next = entry;
			size++;
		}
	}
}

public V get(K key) {
	int hashcode = key.hashCode();
	int address = Math.abs(hashcode % table.length);
	return find(key, address);
}

// linear probing
private V find(K key, int address) {
	for(int i=0; i<table.length; i++) {
		Entry<K,V> current = table[(i+address)%table.length];
		if(current == null) {
			return null;
		} else {
			if(key.equals(current.key)) {
				return current.value;
			}
		}
	}
} 

// Separate Chaining
private V find(K key, int address) {
	Entry<K, V> current = table[address];
	while(current != null && current.key.hashCode() < hashcode) {
		current = current.next;
	}
	if(current == null) {
		return null;
	} else {
		if(current.key == key) {
			return current.value;
		} else {
			return null;
		}
	}
} 
```

Three Cases for Next
1. Smaller
2. Not Smaller
3. Nothing
4. Equal to something

Removing is complicated for shifting hashcodes backed.
