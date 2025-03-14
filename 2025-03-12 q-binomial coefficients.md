Last time: Gaussian q-binomial coefficients
$$[n]_q! := \frac{(1-q)(1-q^2) \cdots (1-q^n)}{(1-q)^n}$$
and
$$\begin{bmatrix}n\\k\end{bmatrix}_q := \frac{[n]_q!}{[k]_q! \cdot [n-k]_q!} $$
**Theorem** (proved by induction):
$$\begin{bmatrix}n\\k\end{bmatrix}_q = \sum_{\lambda \subseteq k \times (n-k)} q^{|\lambda|}.$$
where $k \times (n-k)$ is the set of Young diagrams that fit in a $k$ by $(n-k)$ rectangle.

## Alternate proof
Suppose $q = p^s$. Let $\mathbb{F}_q$ be the field with $q$ elements.

The *Grassmannian* $\mathrm{Gr}(k, n; \mathbb{F})$ is the "variety" of all $k$-dimensional linear subspaces in $\mathbb{F}^n$.
- Note: $\mathbb{F}$ can be any field.
- Think about "variety" as "set" (though there are actually more subtle differences)
- Need $k \le n$.

Example: **the projective line**
- Usually denoted by $\mathbb{P}^1$, is the Grassmannian $\mathrm{Gr}(1, 2; \mathbb{R})$.
	- A single point in this space is a line passing through the origin in $\mathbb{R^2}$.
	- To parameterize these lines, note where it intersects $y=1$.
	- So $\mathbb{P}^1$ is basically just a line... except there's an extra point at $\infty$, which corresponds to the horizontal line in $\mathbb{R^2}$.

How to think about Grassmannians?
- In terms of **matrices**.
- Take $\mathrm{Gr}(k, n; \mathbb{F})$ as the "set" of $k\times n$ matrices $A$ where the entries are in $\mathbb{F}$ where the rank is $k$, **MODULO** row operations
- Corresponds to the rowspace of $A$

If $\mathbb{F}$ is a finite space, we can count how many such matrices exist. This is
- the number of matrices of rank $k$
- divided by the number of invertible $k\times k$ matrices

To pick $A$:
	- First row can be any nonzero vector, i.e. $q^n-1$
	- Second row can be anything not spanned by the first vector, i.e. $q^n-q$
	- Third row can be $q^n-q^2$

In the denominator: same expression, but with $k$ instead of $n$.

Now back to theorem 1 (??)
$$\begin{bmatrix}n\\ k_1, \dots, k_g\end{bmatrix} = \sum_{w: \text{permutation of set }(1^{k_1}, 2^{k_2}, \dots)} q^{\mathrm{inv}(w)} $$

- We can also count the number of matrices in rref form.
- Consider that $\tilde{A}$ is in rref  and has $n-k$ pivot columns. Clean these, d

## More things
With $s=2$, we get that there is a bijection between:
- young diagrams that fit in a $k \times (n-k)$ rectangle
- permutations of the multiset $\{1^k, 2^{n-k}\}$ ($k$ copies of 1, $n-k$ copies of 2)

This is pretty easy---just take the path in the grid that forms the Young diagram and write a 1 for every up step and a 2 for every right step.

Claim: inversions in $w$ are in bijection with boxes of $\lambda$. This makes sense because each box corresponds to a row (up step) and a column (right step) if we draw the hook.