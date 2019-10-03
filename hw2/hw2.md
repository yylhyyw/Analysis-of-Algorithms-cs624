---
export_on_save:
    html: true
---
### CS 624
### Assignment 2
### Yiwei Yao
---
#### 1.
* Algorithm:
    ```
    FIND-SMALLEST-K(A, k)
        BUILD-HEAP(A)
        for i<- K down to 1 do:
            Heap-Extract-MIN(A)
    ```
    First we build a Min-Heap, and then we extract k times of the elements from Min-Heap. After that, we got k smallest elements.
* Time complexity: As we know from the note that build-heap takes O(n), and the run time of Heap-Extract-MIN is the same as the Heap-Extract-MAX which also states in the note and takes log(n) times. In this case, we first build a min heap and then run k times of Heap-Extract-MIN, therefore the time complexity for the algorithm is $O(n+klogn)$
---
#### 2.
* a. In TAIL-RECURSIVE-QUICKSORT version, it actually runs quick-sort twice just like the normal no-tail-recursion quicksort. In TAIL-RECURSIVE-QUICKSORT version, it uses while loop which checks the p value again, and when the left part quick sort recusion was done, the program reassign the p value and do the right part continue.
* when the array is sorted, so we have to call QUICKSORT n times, and have stack depth of n.
* code after modified:
    ```
    QUICKSORT(A, p, r)
        while p < r
            q = PARTITION(A, p, r)
            if q - p < r - q
                QUICKSORT(A, p ,q-1)
                p = q + 1
            else QUICKSORT(A, q + 1, r)
                r = q - 1
    ```
    In this case each recursive calls are reduced by half, the number of recursive calls will be $lgn$ times, thus the stack depth, is at most $lgn$.
---
#### 3.
* Base Case: if a binary tree has depth 0, then it has at most 1 leaf with the node it self and 1 = $2^0$.
* Case of depth 1: if a binary tree has depth 1, then it has at most 2 leaf with one node and 2 = $2^1$.
* Case of depth 2: if a binary tree has depth 2, then it has at most 4 leaf with one root, two sub nodes. and 4 = $2^2$.
* ......
* Induction Hypothesis:  Assume that for depth n >= 0, all binary trees of depth <= n have at most $2^n$ leaves.

* Induction Step:  there is a binary tree of depth n+1. Then the left and right sub node trees are each binary trees of height <= n, and accoring to the induction hypothesis we made that for depth n >= 0, all binary trees of depth <= n have at most $2^n$ leaves. We add up two subtrees: $2^n + 2^n = 2^(n+1)$.  Therefore the hypothesis is true for depth n+1, and the statement is proved.
---
#### 4.
* 6.5-7: For stack: we can push pairs of the elements and the counts of how many elements have inserted into a max-priority-queue and using heap-extract-max to pop. <br> For queue: we also enque pairs of the elements and the counts of how many elements have inserted into a min-priority-queue, and using heap-extract-min to deque.
---
#### 5.
* In the quick sort, partition should look up all the elements, so the run time should be cn. However, when left part of list have done the sorting, the partition will have less elements to look up, so at that case the run time will less than cn.
---
#### 6.
* if sort row first and then sort columns that means we have the smallest number at left-top conor. and the one at its left and the one at its down are bigger than it. In this case, all numbers to its left and down must bigger than it. Thus, after column sort, the row still are sorted.
---
#### 7.
* a. algorithm:
```
divide the list recursively into two parts until there is only one in both parts. 
Then merge the smaller lists with same size into new list in sorted order using super-hardware.
```
* b. $T(n) = 2T(n/2) + \theta(n^c)$
* c. accoring to master theorem, $a=2$, $b=2$,$n^{log_ba}=n$, if $n^c$ < $n$, $c$ < $1$ then this algorithm perform substantially better than $O(nlogn)$. However, to merge two sort lists of length n we have to compare at least n times, therefore, it is highly impossible that this kind of hardware exist.


