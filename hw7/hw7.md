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
* Suppose a disjunctive nomral form $P=c_1\vee c_2\vee ... \vee c_m$. $P$ will be true if one of clauses can be true, what's more if there is $z_i^{(k)} = \neg z_{i+1}^{(k)}$ where $1\leq i< |c_k|$ in any clause $c_k$, then $c_k$ is false. Therefore, an algorithm checks literal in every clause if it exists $z_i^{(k)} = \neg z_{i+1}^{(k)}$ which takes $O(|C|^2)$. In $|P|$ clauses, the algorithm takes $O(|P|*|C|^2)$ times which is satisfiable in polynomial time.
#### 4.
* In order to prove that $SAT \leq_p 3$-$SAT$, it is obvious that there is a function $f$ that maps from $SAT$ to $3$-$SAT$. What's more, for a instance $c$ of $SAT$ to compute $f(c)$ is $O(|c|^k)$ because the worest case is add two new variables to every single literal in $c$ and will take at most $O(|c|^k)$ times.
* Then in otder to prove that instance $c$ of $SAT$ and instance $c'$ of $3$-$SAT$ has the same answer we have to discuess in four cases:
    * $SAT$ instance $C$ has one literal: Let a instance of $SAT$ 
    $C$ has one literal $c_1$, then let $u,v$ be the new variables, we can generate $C'=(c_1\vee u \vee v)\land (c_1\vee u \vee \neg v)\land (c_1\vee \neg u \vee v)\land (c_1\vee \neg u \vee \neg v)$. Therefore, $C'$ is satisfiable if c is satisfiable.
    * $SAT$ instance $C$ has two literals: Let a instance of $SAT$ $C$ has one literal $c_1\lor c_2$, then let $u$ be the new variables, we can generate $C'=(c_1\vee c_2 \vee u)\land (c_1\vee c_2 \vee \neg u)$. Therefore, $C'$ is satisfiable if c is satisfiable.
    * $SAT$ instance $C$ has three literals: Let a instance of $SAT$ $C$ has three literal $c_1\lor c_2\lor c_3$, then $C'$ is satisfiable if c is satisfiable with nothing changes.
    * $SAT$ instance $C$ has more then three literals: Let a instance of $SAT$ $C$ has three literal $c_1\lor c_2\lor c_3\lor ...\lor c_k$, then let $u_1, u_2,...,u_{k-3}$ be the new variables, then $C'=(c_1\lor c_2\lor u_1)\land (c_3\lor \neg u_1\lor u_2)\land (c_4\lor \neg u_2\lor u_3)\land ...\land (c_{k-2}\lor \neg u_{k-4}\lor u_{k-3})\land (c_{k-1}\lor c_{k}\lor \neg u_{k-3})$. Therefore, $C'$ is satisfiable if c is satisfiable.
#### 5. 
* (a) 
    * Suppose $V_2$ is an independent set in $G$, then $G=(V, E)$ is reducible to a vertex cover on $G'= (V_1, E')$ where $V_1=V−V$ because $V_1$ is an independent set, any edges that have one of endpoints in $V_2$ and another endpoints in $V_1$. Therefore, $V_1=V-V_2$ where $V_1$ is vertex cover.
    * On the other hand, suppose $V_2=V-V_1$ is not an independent set, then there must be an edge that both endpoints are in $V_2$ and not in $V_1$. However, there is an contradiction that $V_1$ is a vertex cover of $G$. Therefore, vertex cover $V_1\in G(V, E)$ is reducible to an independent set of vertices $V_2=V−V_1$.
    * Both statements in $1$ can polynomially reducible to each other which means they are equally hard.
* (b) 
    * Suppose an independent set of vertices $V_2$ in an undirected graph $G=(V,E)$, since $V_2$ is an independent set, for any pair of vertices in independent set are not in the edge $E$ but in edge $E'$. Therefore, since all vertices in $V_2$ are connected in $G^c=(V,E')$, they form a clique in $G'$.
    * On the other hand, suppose a clique in $G^c=(V,E')$, $c=(u,v)\in E'$ which means $(u,v)\notin E$, therefore they form an independent set $V_2$ in $G=(V,E)$.
    * Both statements in $2$ can polynomially reducible to each other which means they are equally hard.