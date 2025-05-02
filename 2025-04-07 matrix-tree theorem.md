The Laplacian matrix of a graph is defined here: en.wikipedia.org/wiki/Laplacian_matrix
1. Entry is $\deg(i)$ if $i = j$
2. Entry is $0$ if $i$ and $j$ are not adjacent
3. Entry is $-1$ if $i \neq j$ but they are adjacent

The number of spanning trees of $G$ is
$$ t(G) = \det(\tilde{L})$$
where $\tilde{L}$ is a "reduced Laplacian matrix" and $\det \tilde{L}$ is a "principal cofactor of $L$."

**Corollary:** let $\lambda_1, \dots, \lambda_n$ be the eigenvalues of $L$. Then
$$t(G) = \frac1n \lambda_1 \cdot \lambda_2 \cdot \cdots \cdot \lambda_{n-1}.$$

**Definition.** A matrix $B$ is **totally unimodular** is any minor of $B$ (i.e. determinant of a square submatrix of $B$) is either 1, 0, or -1.

**Theorem.** Let $B$ be any matrix such that every column of $B$ has all zeros except for a single 1 and a single -1. Then $B$ is totally unimodal.

## Calculating number of spanning trees
Example: $G' = K_n$ (all edges a graph of $n$ nodes). The Laplacian matrix is
$$\tilde{L} = \begin{bmatrix} n-1 & -1 & \dots & -1 \\ -1 & n-1 & \dots & -1 \\ \vdots & & & -1 \\ -1 & \dots & -1 & n-1 \end{bmatrix}.$$
This is an $(n-1)\times(n-1)$ matrix. What is the determinant? Observe first that
$$\tilde{L} = n I_{n-1} - J_{n-1}$$
where $J_{n-1}$ is the $(n-1)\times(n-1)$ matrix with all ones. What are the eigenvalues of this matrix?
1. $n-1$ is an eigenvalue
2. All other eigenvalues are zero, with corresponding eigenvectors having sum equal to 0
So the eigenvalues of $\tilde{L}$ are $n$ times the eigenvalues of $I_{n-1}$ minutes the eigenvalues of $J_{n-1}$. (apparently this is something you can do with matrices)

The eigenvalues of $\tilde{L}$ are thus $1, n, n, \dots, n$ where there are $(n-2)$ occurrences of $n$. This means the determinant is
$$n^{n-2},$$
which is expected by Cayley's formula.

## Hypercube graph
$H_d$ is the 1-skeleton of the $d$-dimensional cube.

Examples:
1. $H_1$ is a line segment.
2. $H_2$ is a square
3. $H_3$ is a cube
4. $H_4$ is a four-dimensional cube

Turns out:
1. There is 1 spanning tree on $H_1$
2. 4 spanning trees on $H_2$
3. 384 spanning trees on $H_3$

If the adjacency matrix has eigenvalues $\alpha_1, \dots, \alpha_2$, then the Laplacian matrix
$$L = dI_n - A$$
has eigenvalues $d-\alpha_1, d-\alpha_2, \dots, d-\alpha_n$.

## Product of graphs
Let $G_1 = (V_1, E_1)$ and $G_2 = (V_2, E_2)$. Then define the product
$$G_1 \times G_2$$
to be the graph with:
1. vertices equal to Cartesian product of $V_1$ and $V_2$
2. edges between two vertices $(u, v)$ and $(u', v')$ iff
	1. there is an edge between $u, u'$ and $v = v'$ OR
	2. there is an edge between $v, v'$ and $u = u'$.

It's as if we take all the vertices of $G_1$ and make each one a universe unto itself, that universe being $G_2$. There are also edges that teleport you between corresponding vertices of $G_2$.

**Claim.** If you know the eigenvalues of the adjacency matrices of $G_1$ and $G_2$, you can figure out the eigenvalues of the adjacency matrix of their product.

Turns out: $H_d$ is the product of a bunch of two-chains.

**Lemma.** Let $G$ and $H$ be two graphs. Then the eigenvalues of the adjacency matrix of $G \times H$ are $\alpha_i + \beta_j$ for all $i \in [m], j \in [n]$. where $\alpha_i$ are the eigenvalues of $A(G)$ and $\beta_j$ are the eigenvalues of $A(H)$.

Using the above lemma:
1. $A(H_d)$ has eigenvalues $d-2k$ with multiplicity $\binom dk$ for all $k=0, \dots, d$.
2. $\tilde{L} (H_d) = dI_n - A$ and has eigenvalues $d - (d - 2k) = 2k$ with multiplicity $\binom dk$.

**Theorem.**
$$t(H_d) = \frac1n \lambda_1 \lambda_2 \cdots \lambda_n.$$
So we have
$$t(H_d) = \frac{1}{2^d} \cdot \prod_{k=1}^d (2k)^{\binom dk}.$$
We can pull out all the $2^{\binom dk}$ (notice we have $k=0$ missing though):
$$t(H_d) = 2^{2^d-d-1} \prod_{k=1}^d k^{\binom dk}.$$
