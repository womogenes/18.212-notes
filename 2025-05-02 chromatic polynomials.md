**Definition.** The chromatic polynomial
$$\chi_G(t)$$is defined to be the number of proper $k$-colorings of $G$, for all $k \in \mathbb{Z}_{\ge 0}$.

**Examples.** $\chi_{K_n}(t) = t(t-1)(t-2) \cdots (t-n+1)$


## Chordal graphs
The graph $G$ is **chordal** if **every** cycle $C = (u_1, u_2, \dots, u_n)$ in $G$ with $m \ge 4$ vertices has a chord, i.e. an edge between $u_i$ and $u_j$ not adjacent vertices.

**Definition.** A **perfect elimination ordering** of $G$ is a way to order its vertices
$$(v_1, v_2, \dots, v_n)$$
such that for all $i$, the set of
$$\{v_i \mid j < i \text{ and }v_j\text{ is adjacent to }v_i\}$$
is a clique (i.e. complete subgraph).

Observe you can build such a graph by adding new vertices and connecting them to cliques.

**Theorem.** (Fulkerson-Gross, 1965) A graph $G$ is chordal if and only if $G$ has a perfect elimination ordering.

*Proof.* The reverse direction is easy. Suppose $G$ has a perfect elimination ordering, but it's not chordal. So there exists a cycle of $m \ge 4$ with no chord. In the perfect elimination ordering, take the maximal vertex in this cycle.
- It has two neighbors in the cycle.
- These two neighbors should be connected.
- But they're not, because of assumption, so **contradiction**
The opposite direction:
- Suppose $G$ is chordal. Let's find a perf. elimination ordering.
- Let $v_1, \dots, v_n$ be a perfect elimination ordering of $G$.
- Let $a_i$ be the \# of $j < i$ such that $(v_i, v_j)$ is an edge of $G$
	- i.e. "number of vertices before you that you're connected to"
- The order of the $a_i$ can be different for different perfect elimination orderings of $G$, but it turns out their frequencies are always the same:
  
  **Theorem.** For all graphs $G$ with a perfect elimination ordering,
  $$\chi_G(t) = \prod_{i=1}^n (t-a_i).$$
  *Proof.* Construct: the $i$th vertex can be colored any number of colors except the previous $a_i$, for a total of $(t-a_i)$. **Important!** Notice that the first $a_i$ vertices must all be different colors because the perfect elimination ordering condition stipulates that they a clique and all distinct colors.

## Universal deletion contraction invariant
We want to find an invariant on graphs (a number? polynomial?) that doesn't change if you reorder the vertices.

**Tutte (Tutte-Whitney) polynomial:**
$$T_G(x, y)$$
Is defined on an **undirected** graph $G = (V, E)$. Multi-edges and loops are allowed.

There are many ways to define it.
1. Must satisfy
   $$T_G = T_{G\setminus e} + T_{G/e}$$
   for all edges $e$ that are neither loops nor bridges. (Recall a bridge is something that, if chopped, creates extra connected components.
2. For all bridges $e$,
   $$T_G = x \cdot T_{G\setminus e}$$
3. For all loops $e$,
   $$T_G = y \cdot T_{G/e}.$$
4. $T_G = 1$ if $E = \emptyset.$

*Proof.* The existence part is easy (decompose the graph), but the uniqueness part is nontrivial.

**Corollary.** If $G$ has $i$ bridges and $j$ loops and no other edges, hen $T_G = x^i \cdot y^j.$

*Proof.* If this is the condition, then $G$ looks like a forest with (optionally) some loops.


**Definition.** Whitney's **corank-nullity polynomial** of $G$
$$W_G(x, y) = \sum_{A\subseteq E} x^{k(A)-k(E)} \cdot y^{k(A) + |A| - |V|}$$
where:
- $A$ defines a subgraph $(H = (V, A)$ of $G$ and
- $k(A)$ is the \# of connected components of $A$

Sidenote: it's called corank-nullity because if you express $G$ as a certain type of matrix, the power of $x$ is the corank and the power of $y$ is the nullity (or something like that)

**Theorem.**
$$T_G(x, y) = W_G(x-1, y-1).$$
*Proof.* Check deletion-contraction, condition 2, condition 3, and condition 4 for the Whitney polynomial.

