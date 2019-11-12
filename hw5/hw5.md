---
export_on_save:
    html: true
---
### CS624
### Assignment 5
### Prof. Nurit Haspel
### Yiwei Yao
---
#### 1.
* According to the huffman algorithm, each time we insert a node which repesents the two elements with the lowest frequency in the minimal queue. Let the case that the huffman has the maximal height if the maximal height is greater or equal to $n-1$ then we can find a huffman tree with n nodes whose height is n-1. If we want to generate a huffman tree with the maximal height, the new node that we insert into the queue must be the minimal one always such that we can append the new node onto the existed node with higest height. We inital a huffman tree with $0$ height first, then after each iteration, the height increase by one. at the end after $n-1$ time iterations, we got the maximal height $n-1$. Therefore, there exists a Huffman tree with n nodes whose height is $n-1$.
#### 2.
* Assume a prefix code tree $T$ of the given set $C$ contains an internal node $x$ with $1$ child, in other words, the node $x$ has only left subtree or right subtree $st$ with height $\geq 0$ and the subset $S$. $$AC(T)=\sum_{x\in (C-S)}f(x)*d_T(x)+\sum_{x\in S}f(x)*d_T(x)$$ If we replace the internal node $x$ with its left subtree or right subtree $st$ to construct a new tree $T'$, the only change is $d_{T'}(x) = d_T(x)-1$ since we remove the node $x$ and it will have no influence to other things.$$AC(T')=\sum_{x\in (C-S)}f(x)*d_T'(x)+\sum_{x\in S}f(x)*d_T'(x)$$ Since $d_T'(x)<d_T(x)$, $AC(T)<AC(T')$. Therefore, we have showed that if a tree representing a prefix code contains an internal node with 1 child, then there is a tree with a more efficient prefix code.
#### 3.
* Exercise 10.1-6. Algorithm: Given two stack $S1$ and $S2$
    ```
    ENQUEUE(x):
        PUSH(S1, x)
        S1.length <- S1.length + 1
    ```
    ```
    DEQUEUE():
        if(S2.length == 0):
            for i ← S1.length to 1 do:
                PUSH(S2, S1.pop())
            end for
        end if
        return pop(S2).
    ```
    It is obvious that ENQUEUE(x) takes $O(1)$ time, because it runs PUSH operation each time and PUSH operation takes $O(1)$ time.<br>
    In DEQUEUE operation, the worst case is that the $S2$ is empty. In the worst case, given n elements in $S1$, it takes $O(n)$ times since we have to run n times PUSH in for loop.
*  Exercise 17.3-6. the amortize cost for both ENQUEUE and DEQUEUE is $O(1)$. For ENQUEUE, it is $O(1)$ since it push one element each time, and each push step takes $O(1)$. For DEQUEUE, because we poped all elements from $S1$ and pushed in to $S2$ when we enqueue the first elements, in the rest of dequeue steps we only do pop once. For example, we need to enqueue n elements and when we enqueue first we pop $n$ times and then push $n$ times and pop $1$ time, at senond time of enqueue, we pop $1$ times only so does other enqueues for times less then $n$. Therefore we can get equation $(n+n+1) + \sum_{i=1}^{n-1}1=3n$, the average cost of each enqueue is $3n/n = 3$. Therefore, the amortize cost for both DEQUEUE is $O(1)$.
#### 4.
* In order to pop $min\{k,n\}$ and $min\{k,m\}$ elements from A and B, MultipopA(k) and MultipopB(k) should run the Pop() $min\{k,n\}$ and $min\{k,m\}$ times. Thus, the worst case are $O(n)$ and $O(m)$ for MultipopA(k) and MultipopB(k). What's more, for Transfer(k) operation that either pop k elements from A and push it to B or A is empty, thus the worst case is that we pop k elements from A and push k elements to B which takes $2k$ times in totally and it is $O(k)$. 
* For $PUSH(A, n)$, the operaiton of $PUSH()$ is $O(1)$, therefore, we can generate a equation $\sum_{i=1}^n1=n$ which implies that the amortized cost for $PUSH(A,n)$ is 1. For $TRANSFER(n)$, as we discussed above that the worst case is pop $k$ elements from $A$ and push $k$ elements to $B$, using aggregate method, we cab get a equation $\sum_{i=1}^n(1+1)=2n$ since the pop and push operation takes $O(1)$ on each. Therefore, amortized cost of $TRANSFER(n)$ is $2n/n=2$.