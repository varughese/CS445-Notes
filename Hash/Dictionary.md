## Dictionary

An Entry object

```java
private class Entry<K,V> {
	private K key;
	private V value;
}

Entry<K,V>[] entries = new Entry<K,V>[29];


entries.put(key, fileWriter)

// Keep a LOAD_FACTOR
// size < entries.length * LOAD_FACTOR

```

When we put,
We check capacity and we need to rebalance
Then get the hashcode
Address (hashcode % entries.length)
add to table and resolve collision 

If we have a null key, then we can make its hashcode 0

```java
private void addToTable(int address, Entry<K,V> entry) {
	for(int i=0; i<entries.length; i++) {
		int ndx = (i+address) % entries.length;
		if(entries[ndx] == null) {
			entries[ndx] = entry;
			size++;
			break;
		} else if(entries[ndx].getKey().equals(entry.getKey())) {
			entries[ndx] = entry;
			break;
		}
	}
}
```
