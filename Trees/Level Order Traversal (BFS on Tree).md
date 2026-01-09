### 1. What is Level Order Traversal

Level Order Traversal is a **Breadth First Search (BFS)** technique that processes a binary tree **level by level**, visiting all nodes at depth _d_ before moving to depth _d + 1_. It enables **row-wise processing** of the tree.

---

### 2. How It Works (High-Level Flow)

A queue is used to store nodes of the current level.  
At each iteration, the **initial queue size defines the level boundary**, ensuring only nodes from the same level are processed together before their children are added for the next level.

---

### 3. When to Use

Use Level Order Traversal when:

- The problem requires **level-by-level processing**
    
- You need **minimum depth** or **first occurrence by level**
    
- Computing **aggregates per level** (sum, average, max)
    
- Deriving **left view / right view** of a tree
    

---

### 4. Why BFS Fits This Pattern

BFS naturally groups nodes by depth, providing **explicit level boundaries** and **implicit depth handling**, which makes per-level computation simpler and less error-prone than DFS.

---

### 5. Core Invariant

> At the start of each iteration, the queue contains **exactly all nodes of the current level**, no more and no less.

This is what guarantees correctness.

---

### 6. Java Code Template

```java

Queue<TreeNode> q = new LinkedList<>();
q.add(root);

while (!q.isEmpty()) {
    int size = q.size(); // level boundary

    for (int i = 0; i < size; i++) {
        TreeNode node = q.poll();

        if (node.left != null) q.add(node.left);
        if (node.right != null) q.add(node.right);
    }
}


```



---

### 7. Time & Space Complexity


- **Time:** O(N) — each node is visited once
    
- **Space:** O(W) — where W is the maximum width of the tree

---

### 8. Common Pitfalls

1. Forgetting to add the root node to the queue
    
2. Mixing nodes from different levels by misusing queue size
    
3. Adding null children to the queue

---

### 9. LeetCode Problems

- [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
    
- [111. Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
    
- [1161. Maximum Level Sum of a Binary Tree](https://leetcode.com/problems/maximum-level-sum-of-a-binary-tree/)


---
