
## Binary Tree

Consider the following tree - it will be used in all examples:

![BST](https://i.imgur.com/p0iWIiA.png)


Code to construct it:

	static class Node {
		int val;
		Node left;
		Node right;
		public Node(int val){
			this.val = val;
			this.left = null;
			this.right = null;
		}
	}
	
	static Node construct() {
		Node root = new Node(10);
		root.left = new Node(-5);
		root.left.left = new Node(-10);
		root.left.right = new Node(0);
		root.left.right.right = new Node(5);
		root.right = new Node(20);
		root.right.left = new Node(15);
		root.right.right = new Node(30);
		root.right.right.right = new Node(35);
		return root;
	}

## 1. Search in BST

**Recursive:**

	private static boolean search(Node root, int val) {
		if(root == null)
			return false;
		if(root.val == val)
			return true;
		else if(root.val > val)
			return search(root.left, val);
		else
			return search(root.right, val);
	}

**Iterative:**

	private static boolean search(Node root, int val) {
		while(root != null) {
			if(root.val == val)
				return true;
			else if(root.val > val)
				root = root.left;
			else
				root = root.right;
		}
		return false;
	}

## 2. Tree Traversal

Tree traversals are classified into 2 types: Depth first traversals and Breadth first traversals.

Depth first traversals are:
- Preorder: Visit, Left, Right
- Inorder: Left, Visit, Right
- Postorder: Left, Right, Visit

Breadth first traversals are:
- Level order: Print level by level

### Preorder:

**Recursive**

	static void preorder(Node root, List<Integer> arr) {
		if(root == null)
			return;
		arr.add(root.val);
		preorder(root.left, arr);
		preorder(root.right, arr);
	}

**Iterative**


