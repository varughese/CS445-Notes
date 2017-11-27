# Binary Tree
Look at node. If value greater, move to right. Else move to left child. If no left or right child we add to that spot.


Our tree should be mostly `full` if we throw random data at itl

Layer height


Complete is a full tree minus a node. Nodes moving in from the left to the right.

Not complete.


Number of nodes in a full tree is 2^n-1.


The number of layers is how hard it is to find.



Normal case of finding is `O(log n)`.


Unbalanced tree is when Left Nodes > Right Nodes or Right Nodes > Left Nodes


---

Tree Node
value
leftChild
rightChild


Rightmost left child and Leftmost right child



## Removal
#### 1 - leaf
Just remove the child
#### 2 - one child
Just interchange with the child
#### 3 - two children
Rightmost left child or leftmost right child



### Printing
You just keep going left and then go right

## Tree vs Hash Table
#### Tree
Tree Find Things O(log n)
Easy to Add O(log n)

#### Hash Table
Find Things O(1)
Add Things O(1)

### Trees have Order
Compare



