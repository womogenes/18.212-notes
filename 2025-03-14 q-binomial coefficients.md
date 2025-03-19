Fix $k$. Then the limit as $n$ approaches infinity of
$$\begin{bmatrix}n\\ k\end{bmatrix}_q,$$
you get
$$\frac{1}{(1-q)(1-q^2)(1-q^k)} = \sum_{\lambda\text{ at most }k\text{ rows}} q^{|\lambda|}.$$
If you take the limit as $k$ approaches infinity and $n-k$ approaches infinity of the same thing, you get
$$\sum_{\lambda\text{ all Young diagrams}} q^{|\lambda|} = \prod_{n \ge 1}{\frac{1}{(1-q^n)}},$$
which is due to Euler (1790).

**Definition.** The partition number $p(n)$ is the number of all partitions of $n$.

The numbers go $1, 1, 2, 3, 5, 7, 11, 15, 22, \dots$ Hardy-Ramanujan showed in 1918 that
$$p(n) \approx \frac{1}{4n \sqrt{3}} \cdot e^{\pi\sqrt{\frac{2n}{3}}}.$$
Another thing:
$$\begin{bmatrix}n\\ k\end{bmatrix}_q = \sum_{i=0}^N r_i \cdot q^i$$$r_i$ is the number of Young diagrams with $i$ boxes that fit in a $k \times (n-k)$ rectangle (fix $n$ and $k$)

**Unimodality theorem** (Sylvester 1878): Fix $n$ and $k$. Then
$$r_0 \le r_1 \le \dots r_{\lfloor \frac{N}{2} \rfloor} \ge \dots \ge r_N.$$
*Proof.* Let $V_i$ be the space of formal linear combinations of Young diagrams $\lambda \le k \times (n-k)$ with $i$ boxes. It has dimension $r_i$ because there are $r_i$ such Young diagrams.

We use up and down operators on only Young diagrams in this linear space.
- Weighted up and down iterators.
- Up iterator: $U_i: V_i \rightarrow V_{i+1}$
- Down iterator: $V_i: V_{i+1} \rightarrow V_i$

The up iterator acts linearly by adding a single box:
$$U_i: \lambda \mapsto \sum_{\mu = \lambda\cup\{a\}} \text{wt}(a) \cdot \mu$$
where $a$ is a box to be added and $\text{wt}(a)$ is some weight that we will describe later.

How to define the weights? Unsure yet... but remember that they depend only on the box being added. We can describe each $U_i$ and $D_i$ by a matrix because they are linear operators.
- $U_i = r_{i+1} \times r_i$ matrix
- $D_i = (U_i)^T$.

**Lemma.**
$$D_i \times U_i = U_{i-1} \times D_{i-1} + H_i,$$
where $H_i$ is a diagonal matrix where
$$H_i: \lambda
\mapsto
\left(\sum_{a \in \text{Add}(\lambda))} \text{wt}(a)^2
- \sum_{b \in \text{Remove}(\lambda)} \text{wt}(b)^2 \right)
\cdot \lambda,$$
where $\text{Add}(\lambda)$ is the set of boxes you can add to $\lambda$ and $\text{Remove}(\lambda)$ is the set of boxes you can remove from $\lambda$. Note each side is an $r_i \times r_i$ matrix.

**IF** we can find a weight function $\text{wt}(a)$ such that the expression for $H_i$ is strictly positive for all Young diagrams $\lambda$ with $i$ boxes, then
$$H_i = D_i \cdot U_i - U_{i-1} \cdot D_{i-1}$$
is a diagonal matrix with positive entries. Recall $D_i = (U_i)^T$, and the product of a matrix and its transpose is a positive semidefinite matrix (symmetric and all eigenvalues are nonnegative).

Basically this means if we can satisfy $U_0$ and $D_0$ are positive definite, then everything is positive definite. So we chill ??
- positive definite implies determinant positive
- implies rank = $r_i$ implies
- rank $U_i \ge r_i$
- implies $r_{i+1} \ge r_i$.

Now we just need a weight function such that the inequality holds for all $\lambda$ with $|\lambda| < k \cdot (n-k)$. Construction:
$$\text{wt}(a) = \sqrt{(k+j-i)(n-k+i-j)}$$
if box $a$ is in row $i$, column $j$ within the $k \times (n-k)$ rectangle. We claim that this makes $H_i$ good for all $i = |\lambda| < \frac{k(n-k)}{2}.$

**Lemma.** For any Young diagram $\lambda \subseteq k \times (n-k)$ and weights defined above,
$$\left(\sum_{a \in \text{Add}(\lambda))} \text{wt}(a)^2
- \sum_{b \in \text{Remove}(\lambda)} \text{wt}(b)^2 \right) = k\cdot(n-k)-2\cdot|\lambda|.$$
