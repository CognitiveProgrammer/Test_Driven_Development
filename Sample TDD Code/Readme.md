# Module - 4 : A Sample Unit TDD code in C++

## 4.1 The problem statement
*We need to create binary search tree using TDD mechanism by writing unit tests First. You can read more about Binary Search Tree [Here](https://en.wikipedia.org/wiki/Binary_search_tree). Simple put, a binary search tree(BST) consists of a node, the value of which will be greater than left child and less than right child*

## 4.2 : Code Creation

*The TDD code will follow the 4 steps of TDD as described in Module - 2, It will start will a failing code which will then be used for writing production code, Here are the steps*

### Step-1 : Writing failing Test Code for BST creation
*We'll have to first create a test code for creating a binary search Tree*

```
TEST(BST, CreateTree) {
	// Arrange
	unsigned int firstData = 56;
	// Act
	BSTree *tree = maketree(56);
	// Assert
	EXPECT_NE(tree, nullptr);
}

```
### Step-2 : Writing production code for failing test in Step-1

*The unit tests for testing the value shall be arranged as below*

```
struct BSTree {
	unsigned int nodeData;
	BSTree *left, *right;
};
BSTree * maketree(unsigned int value) {
	BSTree *treePtr = new BSTree;
	treePtr->nodeData = value;
	treePtr->left = treePtr->right = nullptr;
	return treePtr;
}
```
*The production code written in Step -2 will pass the test written in Step - 1*

*once we have successfully passed tests, we know that we can create the tree, now we need to have some mechanism of adding data into the trees. The data can be of 3 types : Less than the node, equal to the node, as well as greater than the node, we'll deal with each time of data by writing tests for all one by one.*

### Step -3: Writing Test code for adding data greater than the data at node
```
TEST(BST, AddGreaterDataToTrees) {
	// Arrange
	BSTree *tree = maketree(56);
	// Act
	AddData(tree,90);
	// Assert
	EXPECT_EQ(tree->right->nodeData, 90);
}
```
### Step -4: Writing Test code for adding data less than the data at node
```
TEST(BST, AddLowerDataToTrees) {
	// Arrange
	BSTree *tree = maketree(56);
	// Act
	AddData(tree, 20);
	// Assert
	EXPECT_EQ(tree->left->nodeData, 20);
}
```
### Step -5: Writing Test code for adding data equal to that of node
```
TEST(BST, AddDataEqualtothatofNode) {
	// Arrange
	BSTree *tree = maketree(56);
	// Act & Asset at same time
	EXPECT_FALSE(AddData(tree, 56));
}
```
### Step -6 : Writing Production Code to Pass these tests
```
bool AddData(BSTree *tree, unsigned int value) {
	if (value > tree->nodeData) {
		tree->right = maketree(value);
		return true;
	}
	else if (value < tree->nodeData) {
		tree->left = maketree(value);
		return true;
	}
	else {
		return false;
	}
}
```

*Note: Now that we have a tree where we can add data, we need to write failing code for finding data in nodes*
### Step -7: Writing Test Code for Finding Data in Tree
```
TEST(BST, AddRandonSetsOfDataInTree) {
	// Arrange
	BSTree *tree = maketree(56);
	// Act
	AddData(tree, 36);
	AddData(tree, 75);
	AddData(tree, 48);
	AddData(tree, 54);
	//Asset
	EXPECT_TRUE(find(tree, 56));
	EXPECT_TRUE(find(tree, 36));
	EXPECT_TRUE(find(tree, 75));
	EXPECT_TRUE(find(tree, 48));
	EXPECT_TRUE(find(tree, 54));
}
```
### Step -8: Writing Production code from finding data in Tree
```
bool find(BSTree * tree, unsigned int value) {
	while (tree != nullptr) {
		if (tree->nodeData != value) {
			if (value < tree->nodeData)
				tree = tree->left;
			else
				tree = tree->right;
		}
		else {
			return true;
		}
	}
	return false;
}

```
### Step -9: Re-Factoring Code - The final step of TDD
*Despite writing all code from Step -1 to Step -9, the test* __AddRandonSetsOfDataInTree__ *will not pass because the implementation of function* __AddData__ *only takes care of root node left and right child and will fail if more number of members are added. This is the benefit of TDD as we know when our code will fail. To pass the test, we'll refactor the code as*
```
bool AddData(BSTree *tree, unsigned int value) {
	if (value > tree->nodeData) {
		if (tree->right == nullptr) {
			tree->right = maketree(value);
			return true;
		}
		else {
			AddData(tree->right, value);
		}
	}
	else if (value < tree->nodeData) {
		if (tree->left == nullptr) {
			tree->left = maketree(value);
			return true;
		}
		else {
			AddData(tree->left, value);
		}
	}
	else {
		return false;
	}
}
```

__I'm stopping here with the very basic BST, to have complete BST we need to have more tests and code, but i guess the code is good enough for demonstration purpose. I hope it helped you in understanding how TDD code is written__
