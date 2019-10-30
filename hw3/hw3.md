---
export_on_save:
    html: true
---
### CS624
<<<<<<< HEAD
### Assignment 3
=======
### Assignment 2
>>>>>>> 65314d81a1b1d1d6d9e0f89a6df55115cb45b465
### Prof. Nurit Haspel
### Yiwei Yao
---
#### 1. Exercise 2.2
<<<<<<< HEAD
If there are $L$ leaves, the binary tree must be a full-complete binary tree so that the depth of this tree will be the smallest. In order to know the smallest depth $H$ of a binary tree with $L$ leaves, the depth $H$ must have at most leaves $L$. From the previous assignment, we have proved that a binary tree has depth n, then it has at most $2^n$ leaves. A binary tree with $L$ leaves have a depth $H\geq logL$, thus the depth of a binary tree with $L$ leaves is $\Omega(logL)$.
#### 2. Question 9.3-5
To use it, just find the median, partition the array based on that median.

* If ii is less than half the length of the original array, recurse on the first half.
* If ii is half the length of the array, return the element coming from the median finding black box.
* If ii is more than half the length of the array, subtract half the length of the array, and then recurse on the second half of the array.
#### 3. Exercise 1.1
If there are more than one edge in a loop, it means that one vertex will appear more than once except the first and last vertex. It is conflict with the definition of a simple loop that it contains no vertex more than once, except for the first and last vertex.
#### 4. Exercise 1.2(need modified)(https://homepage.cs.uri.edu/faculty/hamel/courses/2012/fall2012/csc447/lecture-notes/csc447-ln025.pdf)(page 3)
Assume that $T$ is a tree. Then $T$ is connected with no simple circuits. Hence, if x and y are distinct vertices of $T$, there is a simple path between them. This path must be unique for if there were a second path, there would be a simple circuit in T. Hence, there is a unique simple path between any two vertices of a tree.
#### 5. Exercise 1.3(need modified)
* If there are more than one parent to a vertex, it will have a loop in a rooted tree, and it is conflict with the definition of tree.
*  Every node has 2 children pointers, for a total of 2n pointers. Every node except the root has a parent, for a total of n - 1 nodes with parents. These n - 1 parented nodes are all children, and each takes up 1 child pointer.
#### 6. Exercise 1.4(need modified)
In a rooted tree, if $x != y$, it means x is an ancestor of y or y is an ancestor of x. if x is an ancestor of y and y is an ancestor of x, it means that x and y is same, $x=y$
#### 7. Exercise 1.5(need modified)
In a rooted tree, if $x != y$, it means x is an ancestor of y or y is an ancestor of x.
#### 8. Exercise 1.6(need modified)
because root is ancestor of each node, so that node x and node y at least a unique common ancestor which is root.
#### 9. Exercise 2.2(need modified)
Substitute (3) into (1):
$c=\beta$
Substitute (3) into (2):
$T(n)=c+\alpha k +\beta + \alpha (n-k-1) +\beta + v$
$T(n)=c+\alpha n +2\beta -\alpha + v$
Because $c=\beta$:
$T(n)=c+\alpha n +2c -\alpha + v$
If $\alpha = (2c+v)$:
$T(n)=(2c+v)n+c$
#### 10. Exercise 4.1(need modified)
=======
* If there are $L$ leaves, the binary tree must be a full-complete binary tree so that the depth of this tree will be the smallest. In order to know the smallest depth $H$ of a binary tree with $L$ leaves, the depth $H$ must have at most leaves $L$. From the previous assignment, we have proved that a binary tree has depth n, then it has at most $2^n$ leaves. A binary tree with $L$ leaves have a depth $H\geq logL$, thus the depth of a binary tree with $L$ leaves is $\Omega(logL)$.
---
#### 2. Question 9.3-5
```
black-box-selection(A, p, r, i):
    if p == r
        return A[q]
    q = black-box(A, p, r)
    k = q - p + 1
    If i > k, black-box-selection(A, q-1, r, i-k)
    If i < k, return black-box-selection(A, p, q-1, i)
    If i == k, return A[q]
```
* recursion function for Selection is $T(n)=T(n/2)+O(n)$, because the worest case for black box is linear time. Using master method, $T(n)=O(n)$
---
#### 3. Exercise 1.1
* If there are more than one edge in a loop, it means that one vertex will appear more than once except the first and last vertex. It is conflict with the definition of a simple loop that it contains no vertex more than once, except for the first and last vertex.
---
#### 4. Exercise 1.2
* Assume that $T$ is a tree which has no simple loop. Hence, if x and y are different vertices of $T$ and there is a simple path between them. Thus, this path must be unique. However if there were a second path, there would be a simple loop in T which is a contradition to the definition of tree. Hence, there is a unique simple path between any two vertices of a tree.
---
#### 5. Exercise 1.3
* If there are more than one parent to a vertex, it will have a loop in a rooted tree, and it is conflict with the definition of tree.
* According to the definition of rooted tree that there are simple paths from x to y, which means that there are paths from root to its descendants. It shows that all nodes are connected through the path from root to themselves, thus all nodes have parent except root. What'more from the previous question, we proved that a vertex can have at most one parent. Therefore, we proved that every vertex other than the root has exectly one parent.
---
#### 6. Exercise 1.4
* In a rooted tree, if $x$ is an ancestor of $y$ which means there is a simple path from $x$ to $y$. if $y$ is an ancestor of $x$ which means there is a simple path from $y$ to $x$. If $y \neq x$, it means there must be a loop from $x$ to $y$. However, there is no loop in a root tree, thus, $x = y$.
---
#### 7. Exercise 1.5
* In a rooted tree, $a$ and $b$ are both ancestor of $x$(not root) which means there are simple paths from $a$ to $x$ and $b$ to $x$. If $a\neq b$, then $a$ must have a simple path to $b$, otherwise there is a loop in the tree. Because there is a simple path between $a$ to $b$, so $a$ can an ancester to $b$ or $b$ can be an ancester to $a$.
---
#### 8. Exercise 1.6
* According to the definition of rooted tree, for any node $x$ and $y$, there must be two pathes from root to $x$ and $y$, and root is their common ancestor. 
#### 9. Exercise 2.2
*   Substitute (3) into (1):
    $c=\beta$
    Substitute (3) into (2):
    $T(n)=c+\alpha k +\beta + \alpha (n-k-1) +\beta + v$
    $T(n)=c+\alpha n +2\beta -\alpha + v$
    Because $c=\beta$:
    $T(n)=c+\alpha n +2c -\alpha + v$
    If $\alpha = (2c+v)$:
    $T(n)=(2c+v)n+c$
#### 10. Exercise 4.1
* 1. Because $a$ is an ancestor of $x$ and $a.key$ $\gt$ $x.key$, it means that $x$ must in the left subtree of $a$, and all the descendant of $x$ must in the left subtree of $a$ too. According to the definition of BST, we proved it.
* 2. Accoring to the definition of BST and successor that if $x$ does not have right subtrees then the smallest key greater than $x$ must be its ancestor which means the successor must be an ancestor of $x$. If $x$ has right subtrees then the smallest key greater than $x$ must in its right children which means the successor of $x$ must in its descendant.
* 3. According to the previous question, we know that if $x$ has right subtrees then the smallest key greater than a must in its right subtrees. And the definition of BST shows that the key of it's left subtrees must less than it. Thus, the smallest key greater than $x$ must be the left most node in the right subtrees.
* 4. Accoring to the previous question, we know that if $x$ does not have right subtrees then the successor must be an ancestor of $x$. Then the definition of BST shows that $x$ must in its left subtrees. Thus, the lowest ancestor of $x$ whose left child is also an ancestor of $x$ is the successor of $x$.
* 5. Accoring to previous question, we proved that If the right subtree of $x$ is nonempty, then the successor of $x$ is just the leftmost node in the right tree. Because the successor of $x$ is leftmost node already, it must not have a left child.
* 6. According to the definition of predecessor that predecessor of $x$ is the largest key smaller than $x$. In this case, if $x$ has a left child, it means that the predecessor must in its left subtrees. Also accoring to the definition of BST, the largest node in the left subtree of $x$ must be the rightmost node in the left subtree of $x$.
>>>>>>> 65314d81a1b1d1d6d9e0f89a6df55115cb45b465


