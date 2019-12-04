---
export_on_save:
    html: true
---
### CS624
### Assignment 7
### Prof. Nurit Haspel
### Yiwei Yao
------
#### 1.
* (a) The value of this flow is 18. No, It is not a maximum flow. We can find a maximum flow by using the residual network.

    * First residual network for the flow given:
        * ```dot{style="zoom:0.5"}
            digraph G{
                {rank=same; a}
                {rank=same; s b c t}
                {rank=same; d}
                s[label= s]
                a[label= a]
                b[label= b]
                c[label= c]
                d[label= d]
                t[label= t]
                a->s [label=5 ];
                s->a [label=5 ];
                b->s [label=8 constraint=false];
                d->s [label=5 constraint=false];
                b->a [label=3 ];
                a->c [label=3 ];
                c->b [label=8 constraint=false];
                b->c [label=2 ];
                b->d [label=3 ];
                d->c [label=3 ];
                t->c [label=8 constraint=false];
                t->a [label=5 constraint=false];
                t->d [label=5 constraint=false];
                d->t [label=5 constraint=false];
            }
            ```
    * Augment flow along path s,a,c,b,d,t capacity of this path is 3, so send 3 units of flow on this path.
    * New flow values
        * ```dot{style="zoom:0.5"}
            digraph G{
                {rank=same; a}
                {rank=same; s b c t}
                {rank=same; d}
                s[label= s]
                a[label= a]
                b[label= b]
                c[label= c]
                d[label= d]
                t[label= t]
                s->a [label="10(8)" ];
                s->b [label="8(8)"];
                s->d [label="5(5)"];
                b->a [label=3 ];
                a->c [label="3(3)" ];
                b->c [label="10(5)" ];
                b->d [label="3(3)" ];
                d->c [label=3 ];
                c->t [label="8(8)"];
                a->t [label="5(5)"];
                d->t [label="10(8)"];
            }
            ```
    * New residual network
        * ```dot{style="zoom:0.5"}
            digraph G{
                {rank=same; a}
                {rank=same; s b c t}
                {rank=same; d}
                s[label= s]
                a[label= a]
                b[label= b]
                c[label= c]
                d[label= d]
                t[label= t]
                
                a->s [color=white]
                a->b [color=white]
                a->c [color=white]
                a->t [color=white]
                s->b->c->t [color=white]
                s->d [color=white]
                b->d [color=white]
                c->d [color=white]
                t->d [color=white]
                a->s [label=8 ];
                s->a [label=2 ];
                b->s [label=8 ];
                d->s [label=5 ];
                b->a [label=3 ];
                c->a [label=3 ];
                c->b [label=5 ];
                b->c [label=5 ];
                d->b [label=3 ];
                d->c [label=3 ];
                t->c [label=8 ];
                t->a [label=5 ];
                t->d [label=8 ];
                d->t [label=2 ];
            }
            ```
    * So the maximum flow has value 21
* (b) We can find a minimum cut using the residual network for the maximum flow which we have in the previous. Starting at $s$, $a$ is the only one reachable from $s$. $a, s$ forms one part in the minimum cut. The other vertices form the other set part of the cut. So a minimum cut in this case are the two sets {s, a} and {b, c, d, t}.
#### 2.
* (a) There is a cycle in the form of $A→B→C→D→H→G→F→E→A$, that passes all vertices in the graph and ends in $A$.  Therefore, Graph $1$ has a Hamiltonian Cycle.
* (b) There is a cycle $c$ of the form $A→B→C→I→H→G→A$, that passes all vertices in the graph and ends in $A$. Therefore, Graph $2$ has a Hamiltonian Cycle.
* (c) 
    * At first we should prove that $G$ has a Hamiltonian Cycle $c$ if any vertex $u\in V$ is an endpoint of exactly $2$ edges. Assume $G$ has a Hamiltonian Cycle $c$ that $u$ is an endpoint less than $2$ edges, then $c$ must not be a cycle which has a contradiction. on the other hand if $u$ is an endpoint more than $2$ edges, according to the definition of Hamiltonian Cycle, we can only go through a vertex(excludes starter) once with one edge go into and one edge go out of a vertex, if a vertex has more than $2$ edges which means we visited the vertex more than once which also has a contradition. Therefore, we showed that $G$ has a Hamiltonian Cycle $c$ if any vertex $u\in V$ is an endpoint of exactly $2$ edges.
    * According to the lemma we have proved that $G$ has a Hamiltonian Cycle $c$ if any vertex $u\in V$ is an endpoint of exactly $2$ edges, we know that edge $(G,D), (G, H), (H, I), (I, F), (F, C), (C, B), (B, A), (A, D)$ must be parts of Hamiltonian Cycle because the vertice $\{G, I, C, A\}$ only have two degrees. However, if we want to pass through vertex $E$ and form a cycle, we must go though the vertece that we have visted again. Therefore, graph $3$ has no Hamiltonian Cycle.
#### 3.
* Suppose a disjunctive nomral form $e=C_1\vee C_2\vee ... \vee C_m$. $P$ will be true if one of clauses can be true. Therefore, if there are no literal $z_i$ and $z_j$ in any clauses that $z_j=\neg z_i$. Give an algorithm checks literal in any clause if it exists $z_i = \neg z_{j}$ which takes $O(|C|^2)$. In $|P|$ clauses, the algorithm takes $O(|e|*|C|^2)$ times which is satisfiable in polynomial time.
#### 4.
* In order to prove that $SAT \leq_p 3$-$SAT$, it is obvious that there is a function $f$ that maps from $SAT$ to $3$-$SAT$. What's more, for a instance $C$ of $SAT$ to compute $f(c)=C'$, we have to reduce every clause which takes $O(|C|)$ times, and it is linear.
* Then in order to prove that instance $C$ of $SAT$ and instance $C'$ of $3$-$SAT$ has the same answer we have to discuss in four cases:
    * $SAT$ instance $C$ has one literal: Let a instance of $SAT$ $C$ has one literal $c_1$, then let $u,v$ be the new variables, we can generate $C'=(c_1\vee u \vee v)\land (c_1\vee u \vee \neg v)\land (c_1\vee \neg u \vee v)\land (c_1\vee \neg u \vee \neg v)$. Therefore, $C'$ should be true if $c_1$ is true.
    * $SAT$ instance $C$ has two literals: Let a instance of $SAT$ $C$ has one literal $c_1\lor c_2$, then let $u$ be the new variables, we can generate $C'=(c_1\vee c_2 \vee u)\land (c_1\vee c_2 \vee \neg u)$. Therefore, $C'$ should be true if $c_1$ and $c_2$ are true.
    * $SAT$ instance $C$ has three literals: Let a instance of $SAT$ $C$ has three literal $c_1\lor c_2\lor c_3$, $C'=c_1\lor c_2\lor c_3$Therefore, $C'$ should be true if $c_1$, $c_2$, and $c_3$ is true.
    * $SAT$ instance $C$ has more then three literals: Let a instance of $SAT$ $C$ has three literal $c_1\lor c_2\lor c_3\lor ...\lor c_k$, then let $u_1, u_2,...,u_{k-3}$ be the new variables, then $C'=(c_1\lor c_2\lor u_1)\land (c_3\lor \neg u_1\lor u_2)\land (c_4\lor \neg u_2\lor u_3)\land ...\land (c_{k-2}\lor \neg u_{k-4}\lor u_{k-3})\land (c_{k-1}\lor c_{k}\lor \neg u_{k-3})$. Therefore, $C'$ should be true if each $c_i$ is true.
#### 5. 
* (a) 
    * Suppose $V_2$ is an independent set in $G$, then $G=(V, E)$ is reducible to a vertex cover on $G'= (V_1, E')$ where $V_1=V−V$ because $V_1$ is an independent set, any edges that have one of endpoints in $V_2$ and another endpoints in $V_1$. Therefore, $V_1=V-V_2$ where $V_1$ is vertex cover.
    * On the other hand, suppose $V_2=V-V_1$ is not an independent set, then there must be an edge that both endpoints are in $V_2$ and not in $V_1$. However, there is an contradiction that $V_1$ is a vertex cover of $G$. Therefore, vertex cover $V_1\in G(V, E)$ is reducible to an independent set of vertices $V_2=V−V_1$.
    * Both statements in $1$ can polynomially reducible to each other which means they are equally hard.
* (b) 
    * Suppose an independent set of vertices $V_2$ in an undirected graph $G=(V,E)$, since $V_2$ is an independent set, for any pair of vertices in independent set are not in the edge $E$ but in edge $E'$. Therefore, since all vertices in $V_2$ are connected in $G^c=(V,E')$, they form a clique in $G'$.
    * On the other hand, suppose a clique in $G^c=(V,E')$, $c=(u,v)\in E'$ which means $(u,v)\notin E$, therefore they form an independent set $V_2$ in $G=(V,E)$.
    * Both statements in $2$ can polynomially reducible to each other which means they are equally hard.
#### 6. Midterm 2
* Medians and Order Statistics:
    * algorithm:
        ```
        findMedianOfTwoArray(A, B):
            if sizeof(A) equals 2 and sizeof(B) equals 2:
                return (max(A[1], B[1])+min(A[2], B[2]))/2
            end if
            median_A = A[sizeof(A)/2]
            median_B = B[sizeof(B)/2]
            if median_A equals median_B:
                return median_A or median_B
            end if
            else if median_A is greater than median_B:
                new_A = A[1....sizeof(A)/2]
                new_B = B[sizeof(B)/2.....n]
                findMedianOfTwoArray(new_A, new_B)
            end if
            else if median_A is less than median_B:
                new_A = A[sizeof(A)/2.....n]
                new_B = B[1......sizeof(B)/2]
                findMedianOfTwoArray(new_A, new_B)
            end if
        ```
    * Running time:
        In the case of median of A and median of B are different, the algorithm divides the total length of 2 arrays into half until there are only two elements in the array of A and B. Therefore, assume the sum of numbers of two arrays are n, we can generate a recurrence $T(n)=T(n/2)+T(1)$, using master theorem, $T(n)=O(logn)$
* Binary Search Trees:
  * (a)
    * algorithm:
        ```
        sort(A):
            for i <- 1 to n:
                Insert(A[i])
            end for
            M = Minimum(A)
            print M
            for i <- 2 to n:
                print successor(A,m)
            end for 
        ```
    * In my algorithm, it runs Insert for n times, Minimum 1 time, and successor n-1 times. In total, $cost = nlogn + logn + (n-1)logn$. Thus, this sort operation takes O(logn) time.
  * (b)
    * Assume $b_n$ is the left subtree of a binary tree with n nodes, then it must have k nodes with in $\{0\leq k\leq n-1\}$, then in the right subtree of this binary tree has nodes $n-k-1$ nodes where $1$ for root. then the possible of this binary tree is $b_k*b_{n-k-1}$. Sum up all possibles we can get the equation $b_n=\sum^{n-1}_{k=0}b_kb_{n-1-k}$
* Dynamic Programming:
    * (a)
      for 2 nodes:
      ```dot{style="zoom:0.5"}
              graph G{
                  1[label= 1]
                  2[label= 2]
                  3[label= 1]
                  4[label= 2]
                  1 -- 2
                  4 -- 3
              }
      ```
      for 3 nodes:
      ```dot{style="zoom:0.5"}
              graph G{
                  1[label= 1]
                  2[label= 2]
                  3[label= 3]
                  4[label= 1]
                  5[label= 2]
                  6[label= 3]
                  7[label= 1]
                  8[label= 2]
                  9[label= 3]
                  10[label= 1]
                  11[label= 2]
                  12[label= 3]
                  13[label= 1]
                  14[label= 2]
                  15[label= 3]
                  1 -- 2 -- 3
                  5 -- 4
                  5 -- 6
                  9 -- 8 -- 7
                  10 -- 12 -- 11
                  15 -- 13 --14
              }
      ```
    * (b):
        | n   | 1 | 2 | 3 | 4  |
        |-----|---|---|---|----|
        | $b_n$ | 1 | 2 | 5 | 14 |
    * (c):
        * algorithm:
            ```
            DP[0] = 1
            findNumOfBinaryTree(n):
                if DP[n] is set:
                    return DP[n]
                else:
                    for i <- 0 to n-1:
                        DP[n] += findNumOfBinaryTree(i) * findNumOfBinaryTree(n-1-i)
                    end for
                end if
            ```
        * Run Time:
            The findNumOfBinaryTree function runs for loop for n times and each time calls findNumOfBinaryTree function of input i and findNumOfBinaryTree function of input n-1-i. Thus, the algorithm runs $n*(i+(n-1-i))$ times which are $O(n^2)$ times.
* Greedy Algorithm:
    * (a) Let's say $S$ is an optimal solution, Given that a station $s$ is part of $S$. Then there is a station $a$ that covered more parts of road intervals than $s$, then we can find a solution $A$ that covers all stations and even covers more. However, it is a contradiction that $S$ is an optimal solution. Thus there isn't a case that a station $a$ can cover more than station $s$.
    * (b) Because western most house $a$ must be covered, there must be an interval in out set that contains the first station $s$ that puts at the $4$ miles to the western most house. Thus, the internal $[a, a+4]$. Otherwise we replace with $[a-4, a]$, the house $a$ still covered, but we moved the first internal to the right. So it must cover everything cover before and even more. Applying this argument to the rest of the intervals. We can prove that this greedy algorithm gives the optimal solution.
