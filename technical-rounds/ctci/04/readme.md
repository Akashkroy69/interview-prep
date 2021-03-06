
### 1. Given graph find if there is path between 2 nodes

Either use BFS or DFS

### 2. Given sorted list create binary tree with min height

Leetcode 108.

Logic:
- Mid = root
- root.left = a(0...mid-1); root.right = a(mid+1...hi)
- Do while lo<=hi

Code:

    
    private TreeNode create(int[] nums, int lo, int hi) {
        if (lo>hi)
            return null;
        int mid = (lo+hi)/2;
        TreeNode t = new TreeNode(nums[mid]);
        t.left = create(nums, lo, mid-1);
        t.right = create(nums, mid+1, hi);
        return t;
    }
    
    public TreeNode sortedArrayToBST(int[] nums) {
        TreeNode t = create(nums, 0, nums.length-1);
        return t;
    }

### 3. Given binary tree create list of lists containing nodes according to depth

Level order traversal (102) leetcode

Logic: 

- Create list of lists res. Then call helper function passing res, root and level of root (0)
- In helper, check if res has a list at given index. If not, create list and add to res. Add value to the list at given level
- Call helper for children incrementing current level

Code:

    private void traverse(List<List<Integer>> res, TreeNode root, int level) {
        if (root == null)
            return;
        if(level >= res.size()) {
            List<Integer> li = new ArrayList<>();
            res.add(level, li);
        }
        res.get(level).add(root.val);
        traverse(res, root.left, level+1);
        traverse(res, root.right, level+1);
    }
    
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();
        traverse(res, root, 0);
        return res;
    }

### 4. Check if binary tree is balanced

Leetcode 110.

Method 1: Get height of left, right. If it is more than 1, return false else return true. This is O(n logn) because every time we visit a node, we check the height in logn time.

    private int getHeight(TreeNode root) {
        if(root == null)
            return -1;
        else
            return Math.max(1+getHeight(root.left), 1+getHeight(root.right));
    }
    private boolean check(TreeNode root) {
        if(root == null)
            return true;
        if( Math.abs(getHeight(root.left) - getHeight(root.right)) > 1 )
            return false;
        else
            return check(root.left) && check(root.right);
        
    }
    
Method 2: If root = null height = -1. Get height of left and right. If either left or right is unbalanced, return -2. Otherwise check if current node is unbalanced. If it is, return -2 otherwise return height. This is O(n) because every time we visit the node we get the height in constant time.

    private int height(TreeNode root) {
        if(root == null)
            return -1;
        int l = height(root.left);
        int r = height(root.right);
        if(l==-2||r==-2)
            return -2;
        if(Math.abs(l-r) > 1)
            return -2;
        return Math.max(l,r)+1;
    }
    public boolean isBalanced(TreeNode root) {
        if(height(root) == -2)
            return false;
        else 
            return true;
    }

### 5. Validate BST

Leetcode 98

Logic: Give min and max value. Recurse left and right.

    private boolean valid(TreeNode root, long min, long max) {
        if(root == null)
            return true;
        if(root.val > min && root.val < max)
            return( valid(root.left, min, root.val) && valid(root.right, root.val, max) );
        else
            return false;
    }
    
    public boolean isValidBST(TreeNode root) {
        return valid(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }

### 6. Next node

See CTCI (Doubt)

### 7. Build Order

See CTCI (Revise topological sort - DO THIS LATER)

### 8. Lowest common ancestor

Method 1: Create map mapping node to parent. Get height and traverse up. Complexity is O(h)

Follow up: What if you cannot use a data structure?

Logic:

- f(root, p, q) returns lowest common ancestor
- if root = p or root = q or root = null
    - return root
- Check if p is in the left subtree, check if q is in the left subtree
- If p,q are in different subtrees return root
- Otherwise recurse f(root.left, p, q) or f(root.right, p, q) depending on what subtree p,q are present in.

Complexity: O(n^2) because each time we go to a node, we check entire tree and if tree is unbalanced it is n+n-1+n-2...

### 9. BST sequences: DOUBT

### 10. Check Subtree: Check if T2 is a subtree of T1.

- Traverse through T1. if current == t2.root, check

### 11. Random node from BST: Get a node at random from a bst: DOUBT

### 12. Paths with Sum: Doubt
