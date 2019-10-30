---
export_on_save:
    html: true
---
### CS624
### Assignment 3
### Prof. Nurit Haspel
### Yiwei Yao
---
#### 1. Exercise 2.2
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


