#### Assignment 1<br>Yiwei Yao

1. Exercise C.1-15 (page 1189) Hint: use a generating function and differentiate.   
- Solution:   
  - According to generating function, we know that $(1+x)^n = \sum_{k=0}^{n} \binom{n}{k}x^k$, and base on differentiation on $x$ of the equation above, we got $n(1+x)^{n-1}=\sum_{k=0}^{n} \binom{n}{k}kx^{k-1}$, when $x=1$, $n*2^{n-1}=\sum_{k=0}^{n} \binom{n}{k}k$
2. Decide whether each of the following statements is true or false and prove that your conclusion is correct.
   - $2n+1 = O(2n)$ 
   - $f(n) = O(g(n))\ implies\ 2^{f(n)} = O(2^{g(n)})$   
- Solution:
    - $2n+1 = O(2n)$ is true, because the numbers $c=2$ and $n_0=2$ work. when $n\geq 2, 2n+1\leq 2*2n$
    - $f(n) = O(g(n))\ implies\ 2^{f(n)} = O(2^{g(n)})$ is not true, because when $f(n)=2n$ and $g(n)=n$, it does not implies $2^{2n} = O(2^n)$, because $2^{2n}=4^n$, which is clearly not equal to $O(2^n)$.
3. Prove that $log_ax=O(log_bx)$ for any $a\gt 0$ and $b\gt 0$.
- Solution:
  - By the prove on the note of Leture 2, we know that $log_ax=log_bx*log_ab$. So, we find that the if the number $c\leq log_ab$, then $log_ax\leq log_bx*c$, for all sufficiently large $x$.
4. Prove that if $f=O(g)$ and $g=O(h)$ then $f=O(h)$.
* Solution:
  * by the rough meaning of $f=O(g)$, we know that there is some constant $a>0$ such that $f\leq ag$ for all sufficiently large $g$. meanwhile, $g=O(h)$ means some constant $b>0$ such that $g\leq bh$ for all sufficiently large $h$. Substitute $g\leq bh$ into $f\leq ag$, we can get a constant $c=a*b$ such that $f\leq a*b*g=c*g$.
5. Problem 4-1 (a, b, c, f, g) (page 107).
  - Solution:
     - a. For $T(n)=2T(n/2)+n^4$, we have $a=2,b=2,f(n)=n^4$, so $n^{log_ba}=n$. Since $f(n)=n^4$, we have $f(n)=\Omega (n^{log_ba+\varepsilon})$ for $0<\varepsilon<1$. That is, we need to show that there is some constant $c$ with $0\lt c\lt 1$ and some $n_0$ such that for all $n\gt n_0$, $af(n/b)\leq cf(n)$ that is, $2f(n/2)\leq cf(n)$ that is, $2(n/2)^4\leq cn^4$ or equivalently, $n^4/8\leq cn^4$ This certainly holds for any $c\lg1/8$. So we could take $c=1/4$, for example. Therefore we really are in Case 3, and the conclusion is $T(n)=\Theta(n^4)$
     - b. For $T(n)=T(n/10)+n$, we have $a=1,b=10,f(n)=n$, so $n^{log_ba}=n^0=1$. Since $f(n)=n$, we have $f(n)=\Omega (n^{log_ba+\varepsilon})$ for $0<\varepsilon<1$. That is, we need to show that there is some constant $c$ with $0\lt c\lt 1$ and some $n_0$ such that for all $n\gt n_0$, $af(n/b)\leq cf(n)$ that is, $f(n/10)\leq cf(n)$ that is, $n/10\leq cn$ This certainly holds for any $c\lg 1/10$. So we could take $c=1/4$, for example. Therefore we really are in Case 3, and the conclusion is $T(n)=\Theta(n)$
     - c.For $T(n)=16T(n/4)+n^2$, we have $a=16,b=4,f(n)=n^2$, so $n^{log_ba}=n^2$. Since $f(n)=n^2$, we are clearly in Case 2. Therefore the conclusion is that $T(n)=\Theta(n^2logn)$
  
     - f.For $T(n)=2T(n/4)+\sqrt{n}$, we have $a=2,b=4,f(n)=n^{1/2}$, so $n^{log_ba}=n^{1/2}$. Since $f(n)=n^{1/2}$, we are clearly in Case 2. Therefore the conclusion is that $T(n)=\Theta(n^{1/2}logn)$
     - g.For $T(n)=T(n-2)+n^2$, we cannot apply master theorem. while $n=n-2$, $T(n-2)=T(n-4)+(n-2)^2$, while $n=n-3$, $T(n-4)=T(n-6)+(n-4)^2$......Until $n=4$, $T(4)=T(2)+16$. Therefore, $T(n)=n^2+......+4^2\le ((n-4)/2+1)n^2$, $T(n)>(n/2)^2(n-n/2)/2+1$. we got $T(n)=\Theta(n^3)$
6. Problem 4.2 in Lecture notes 1 (page 7).
  - Solution: $T(n)=\sum_{j=2}^n(a+(j-1)c)=\sum_{j=2}^na+\sum_{j=2}^n(j-1)c$, since we know from the note that $\sum_{j=2}^na=\sum_{j=1}^na-\sum_{j=1}^1a=(n-1)a$, and $\sum_{j=2}^n(j-1)c=\sum_{j=2}^{n-1}jc=\frac{cn(n-1)}{2}$. Thus $T(n)=\sum_{j=2}^n(a+(j-1)c)=(n-1)a+\frac{cn(n-1)}{2}=\frac{c}{2}n^2-(\frac{c}{2}+a)n-a=An^2+Bn+C$, when $A=\frac{c}{2}, B=-(\frac{c}{2}+a), C=-a$.
7. Problem 4.1 in Lecture notes 2 (page 12).
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
8. Exercise 6.5-8 (page 166). Note that the problem asks you to give an algorithm that runs in $O(logn)$ time. So you not only have to give the algorithm, you also have to show that it really does run in $O(logn)$ time.
  - Solution:
  ```
  HEAP-DELETE(A, i):
    A[i] = A[heapsize]
    heap-size -= 1
    while(i > 1 and A[parent(i)] < a[i])
        switch A[i] with A[parent(i)]
        i = Parent(i)
    MAX-HEAPIFY(A, i)
  ```
  as we know from the book, the time cost by MAX-HEAPIFY(A,i) is $O(log_n)$, and for while loop, the worest case is to check all nodes and it is the hight of the tree which is logn times. Therefore, the algorithm runs in $O(logn)$ times.

1.  Exercise 6.5-9 (page 166). Another hint: Think of the merging part of MergeSort and extend it to multiple lists. Remember that the lists are not necessarily the same size.
  - Solution:
    - create a size k heap, and then insert all the index of k lists, after that, we do a delete-min operation to find the min elements and put them into a new list until list is empty, than repeat the steps until all k lists are empty.<br>Create a size k min-heap runs in logk times and delete-min runs in constant times as we know from book, because we have to repeat the steps for n times, so the total run time is (nlogk).
