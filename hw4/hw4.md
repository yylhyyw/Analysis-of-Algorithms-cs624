---
export_on_save:
    html: true
---
### CS624
### Assignment 4
### Prof. Nurit Haspel
### Yiwei Yao
---
#### 1. Solve the midterm, see attached pages.
---
#### 2. Exercise 15.4-1 in the text (page 396)(need change)
* An LCS is h1, 0, 1, 0, 1, 0i. A concise way of seeing this is by noticing that the first list contains a “00” while the second contains none, Also, the second list contains two copies of “11” while the first contains none. In order to reconcile this, any LCS will have to skip at least three elements. Since we managed to do this, we know that our common subsequence was maximal.
---
#### 3. Exercise 3.2 in the Lecture 8 handout (on page 8)(need change).
* [If T' is an immediate subtree of T then the $depth_T(k_i)=1+depth_{T'}(k_i)$](https://www.youtube.com/watch?v=UayzCmCp06M)
---
#### 4. Exercise 3.3 in the Lecture 8 handout (on page 10)
* Given a binary search tree with key {$k_i,...k_j$} and node {$k_r$}, we can find its two subtrees, left subtree with keys {$k_i,...,k_r-1$}, and right tree {$k_r+1,...,k_j$}. If we the left subtree and right subtree cannot form a contiguous sequence on each other then there must be a node $k_x$ for $i\leq x\geq r-1$ in right subtree or a node $k_y$ for $r+1\leq x\geq j$ in left subtree. However, it will contradict the assumption that T was a binary search tree. Therefore, the keys in any subtree can form a contiguous sequence.
---
#### 5. Exercise 15-2 (page 405).Longest palindrome subsequence(need change)
* Let A[1..n] denote the array which contains the given word. First note that for a palindrome to be a subsequence we must be able to divide the input word at some position i, and then solve the longest common subsequence problem on A[1..i] and A[i + 1..n], possibly adding in an extra letter to account for palindromes with a central letter. Since there are n places at which we could split the input word and the LCS problem takes time O(n2), we can solve the palindrome problem in time O(n3).
* Algorithm:
```
longest_palindrome(A):
    for i <- 0 to A.length do:
        length[i][i] = 1
    end for
    for i <- 0 to A.length-2 do:
        if A[i] = A[i+1]
            visited[i][i+1] = 2
        else
            visited[i][i+1] = 1
        end if
    end for
    while A.length >= 3
        for i <- 0 to (n -3)
        j = i + length - 1
        if A[i] == A[j]
            visited[i][j] = 2 + 
```
#### 6.
* In the drawn graph above, there are edges {($v_1$,$v_2$), ($v_1$,$v_5$), ($v_2$,$v_4$), ($v_2$,$v_5$), ($v_3$,$v_4$), ($v_4$,$v_5$)}. According to the algorithm given, we find edge ($v_1$,$v_2$), and set w to $v_2$, L to $1$, find ($v_2$,$v_4$), set w to $v_4$, L to $2$, find ($v_4$,$v_5$) set w to $v_5$, L to $3$, then there is no edge out from $v_5$, so the longest path is $3$ which is true.
* In general, there could be a DAG that have edges{($v_1$,$v_2$), ($v_1$,$v_3$), ($v_3$,$v_4$), ($v_4$,$v_5$), ($v_2$,$v_5$)}, in this example, we find the longest path is $2$ that are {($v_1$,$v_2$), ($v_2$,$v_5$)}by using the algorithm above, however, it is wrong, the correct answer is $3$ that are {($v_1$,$v_3$), ($v_3$,$v_4$), ($v_4$, $v_5$)}.
* By considering all possible paths from $v_1$ to $v_n$, there will be exponentially many in $n$, and therefore it is impossible to compare them all if n is large, like $500$.
* Algorithm: 
$LongestPath()$
&emsp;Push $v_1$ into visited[]. visited[] is an array stores the vertex that has been visited.
&emsp;$w \leftarrow visited.pop$ w is the current node we are considering.
&emsp;For n elements in $distance[]$ do:
&emsp;&emsp;$distance[i] \leftarrow 0$. which initialize the distance from $v_1$ to $v_i$ to 0.
&emsp;For each edge out of w do:   
&emsp;&emsp;$distance[v_j]=MAX(distance[v_j], distance[w]+1)$
&emsp;&emsp;push $v_j$ into visited.
&emsp;&emsp;If there is no edge out of w anymore do:
&emsp;&emsp;&emsp; $w \leftarrow visited.pop$.
&emsp; return $distance[v_n]$
The algorithm keep track the max length of path from current vertex to the $v_1$ by storing and updating when we find a edge to the current vertex.
* It takes n times to initialize the distance value of each vertex at first, and then traversing all the edges that is a path or subpath from $v_1$ to $v_n$ to update the distance of each vertex to $v_1$ which is at most $E$ edges. Therefore, the running time is $O(|V|+|E|)$.
---
#### 7.(need improve)
* Suppose that a given G was not the MST from $n_{ik}$ to $n_b$ Then there would be a less weight one—let’s call it Q′. But then if we follow the original path from $n_1$ to $n_ik$ and then switch to the path Q′ from nik to nb, the total cost of all the edges on that path will be less than the cost of the original path P. And that is a contradiction because we assumed that P had the least cost of any path from $n_a$ to $n_b$.
* Assume that there is an MST T that does not contain e. Adding e to T will produce a cycle, that crosses the cut once at e and crosses back at another edge e' . Deleting e' we get a spanning tree T∖{e'}∪{e} of strictly smaller weight than T. This contradicts the assumption that T was a MST. 
* A lightest edge in graph G must be the lightest edge in some cuts of the graph G. According we have proved in the previous problem we know that the lightest edge must be a part of MST of graph G. 
#### 8.(first draft)
* If A is a maximum independent subset of tree T containing x, then A' = A-{x} is an independent subset of T' = T - {x}. Let's assume if A' is not the maximum independent subset of tree T', then it is a contradiction because if we add back {x}, then the maximum independent set will be larger than A.
* Let 𝐼 be a maximum-cardinality independent set containing the greatest number of leaves of 𝑇 of all such independent sets. Suppose that 𝑣∉𝐼 for some leaf 𝑣 of 𝑇 and let 𝑤 be 𝑣's unique neighbour. If 𝑤∉𝐼, then 𝐼∪{𝑣} is independent, contradicting the supposed maximality of 𝐼. Otherwise, 𝑤∈𝐼 but 𝐼′=(𝐼∖{𝑤})∪{𝑣} is an independent set of the same cardinality as 𝐼. Since 𝑇 has at least three vertices, 𝑤 has degree at least two, so is not a leaf. Therefore, 𝐼′ contains one more leaf than 𝐼, again contradicting the choice of 𝐼.
* Algorithm:
```
1: I = ∅, V 0 = V
2: while V' != ∅ do
3:  Choose v ∈ V'(in lexicographically order)
4:  I = I ∪ v
5:  V' = V'\(v ∪ Neighbor(v)
6: end while
7: Return I
```
<div style="page-break-after: always;"></div>

### Midterm Exam 1 
#### 1. Order of growth.
(a) Base Case: $T(4) = d \leq c*4^2*log4=32c$ for the right choice of $c$.
(b) Inductive hypothesis: Assume $T(k) \leq ck^2logk$ for any $k < n$
(c) Substitute  in the equation to prove for $n$.
$T(n) \leq 16(c*(\frac{n}{4})^2log\frac{n}{4})+n^2$
$=cn^2*(logn-2)+n^2$
$=cn^2logn-n^2(2c-1)$
$\leq cn^2logn$ for every $c\geq 1/2$
#### 2. Sorting.
* Quick sort:
Using the example:$4,8_1,8_2,4$
Doing the partition we will remain the first 3 elements same after finishing the for-loop, and it will look like this:
$^p|4^i|8_1|8_2|4^r|$
For the step after for loop we need to switch $i+1$ and $r$. Which will change the order of equal value of keys and will be look like this:
$|4|4|8_2|8_1|$
* Heap Sort:
For example a max-heap looks like 
$3, 2, 1^1, 1^2, 0$. Doing a heap sort on this, it will extra the maximum number from the max-heap, and put into the last index in a new array, after doing it recursively, the sorted array will be $0, 1^2, 1^1, 2, 3$. It exchanges the position of same value, therefore it is not stable.
It does not preserve the order of elements and hence can't be stable
#### 3. Sorting:
* We can get the algorithm by modifying partition part in quick sort:
```
rearrange(A, p, r):
    x <- 0
    i <- p-1
    for j <- p to r do:
        if A[j] < x then
            i <- i+1
            exchange A[i] <-> A[j]
```
In the previous algorithm, it has the same run time as partition in quick sort and we know from the class that the run time is $O(n)$ because it runs maximum n times in the for loop.
#### 4. Heaps:
* Yes, it can.
* According to the definition of heaps. A min-heap is that the key at each node is less that or equal to the key in any descendant of that node which means for any node $i$, the value of node $2i$ and $2i+1$ must greater or equal to the value of node $i$. In other word, $i\leq 2i \leq 2i+1$ for any $i\geq 1$, a sorted array fits the property of min-heap which is that $i\leq i+1\leq i+2......$ for array $i\geq 1$ because $2i\geq i+1$ for $i\geq 1$.