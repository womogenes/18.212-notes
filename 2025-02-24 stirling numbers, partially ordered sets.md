**Theorem.**
1. $$\sum_{k=0}^n s(n,k) \cdot x^k = (x)_n$$
2. $$\sum_{k=0}^n S(n,k) \cdot (x)_k = x^n$$
Recall that $(x)_k$ is a **falling factorial**.

**Proof of second equation.** We will show that the two polynomials on either side are the same for infinitely many values of integer $x$. This proves that the two polynomials are the same.
1. The RHS counts the number of functions from $\{1, \dots, n\}$ to $\{1, \dots, x\}$.
2. The LHS is
   $$\sum_{k=0}^n k! \cdot S(n,k) \cdot \binom{x}{k}$$
   by $(x)_k = k! \cdot \binom{x}{k}.$
3. The product $k! \cdot S(n,k)$ is the number of **ordered set partitions** of $[n]$ into $k$ blocks, which is also the number of surjective maps $f: [n] \rightarrow \{i_1, \dots, i_k\}$
4. $\binom{x}{k}$ is the number of ways to pick the image

Actually this is quite simple lmao it's just a way of counting functions from $\{1, \dots, n\}$ to $\{1, \dots, x\}$ by casework on the size of the image of the function.

## Sperner's theorem (1928)
Let $I_1, \dots, I_N$ be different subsets of $[n]$ such that for all $i \neq j$, neither $I_i$ is contained in $I_j$ or vice versa. Then
$$N \le \binom{n}{\lfloor n/2 \rfloor}.$$
### Posets (partially ordered sets)
$P$ is a set with a binary relation $a \le b$. Axioms:
1. $a \le a$ for all elements $a$
2. If $a \le b$ and $b \le a$, then $a = b$
3. If $a \le b$ and $b \le c$, then $a \le c$

Notation:
- $a < b$ means $a \le b$ and $a \neq b$
- $a \lessdot b$ ("$a$ is covered by $b$" or "$b$ covers $a$") means $a < b$ and there is no $c$ such that $a < c < b$.

If our poset is finite, the complete set of covering relations recovers the poset.
- However, if it's infinite, this may not be true. Take the real numbers, for instance, which have no covering relations.
### Hasse diagram
Graph where nodes are items in the poset and edges are cover relations.
### Chains
If there is a maximal element (an element that is greater than all elements), it is denoted $\hat{1}$.
If there is a minimal element, denoted $\hat{0}$.

$a, b \in P$ are **incomparable** if neither $a \le b$ nor $b \le a$.

A **chain** $C$ in a poset is a subset of elements such that any two elements of $C$ are comparable.
A **saturated chain** is one where you can't squeeze in any more elements.

An **antichain** $A \subset P$ is a subset such that any two elements are incomparable.

We say a poset is **ranked** if it has a "rank function" $f: P \rightarrow \mathbb{Z}$ such that for any covering relation $a \lessdot b$,
$$f(a) + 1 = f(b).$$
For a finite poset, we assume that the ranks go from $0$ to $\ell$.

For a ranked poset $P$, let
$$P_i = \{a \in P \mid f(a) = i\}$$
and
$$r_i = |P_i|$$
("rank numbers").

**Definition.** A finite ranked poset is 
- rank-symmetric if $r_i = r_{\ell-i}$ for all $i = 0, \dots, \ell$.
- unimodal if $r_0 \le r_1 \le r_2 \le \dots \le r_s \ge r_{s+1} \ge \dots \ge r_{\ell}$.
- Sperner if the maximal size of an anti-chain is exactly $\ell$.

### "Boolean lattice"
$B_n$ is the poset of all subsets $I \subseteq [n]$ ordered by inclusion. This is equivalent to all binary $n$-tuples.

**Theorem.** The Boolean lattice is rank-symmetric.