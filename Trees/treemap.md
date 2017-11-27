Map's are put
Set's are add


``` java
public class TreeMap {
	private TreeNode root;
	private int size;
	public void put(Comparable key, Object value) {
		/*
		 * Why do we wait to add the Node?
		 * Because we want to avoid Duplicates
		 * A MultiMap is one key to many values
		 */
		if(root == null) {
			root = new TreeNode(key, value);
			size++;
		} else {
			put(root, key, value);
		}
	}

	private void put(TreeNode node, Comparable key, Object value) {
		int c = key.compareTo(node.getKey()); // should check for nulls
		if(c==0) {
			node.setKey(key); // defensive programming, in case key is different
			node.setValue(value);
		} else if(c < 0) {
			if(node.hasLeftChild()) {
				put(node.getLeftChild(), key, value);
			} else {
				node.setLeftChild(new TreeNode(key, value));
				size++;
			}
		} else {
			// ... same shit
		}
	}

	public Object get(Comparable key) {
		return get(root, key);
	}

	private Object get(TreeNode node, Comparable key) {
		int c = key.compareTo(node.getKey());
		if(c == 0) {
			return node.getValue();
		} else if(c<0) {
			if(node.hasLeftChild()) {
				return get(node.getLeftChild(), key);
			}
			return null;

		} else {
			// .. same shit
		}
	}

	

}


```