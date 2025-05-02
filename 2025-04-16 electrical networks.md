Setup:
- Graph $(V, E)$ of node sin an electrical network
- Edges are resistors, weight of each edge is $1/R$
- Some nodes are hooked up to power, which provides a voltage differential

To talk about current, we must define edge directions (so that signs make sense)
- These can be arbitrary

For every edge $e \in E$:
- resistance $R_e > 0$
- current $I_e \in \mathbb{R}$
- voltage $V_e \in \mathbb{R}$
For each edge $e$, the reverse edge $-e$ has reversed current and voltage.

Three laws:
1. Kirchhoff's first law: for every vertex, current in equals current out
2. Kirchhoff's second law: in any closed loop, voltage is zero
3. Ohm's law: $V_e = I_e \cdot R_e$ for all edges $e$

The second law equates to the existence of a potential function $U: V \rightarrow \mathbb{R}$
- For all edges $e = (u, v)$, $V_e = U_v = U_u$
- Potential function is unique up to moving everything up or down

We can write the potential function as a vector (element $i$ is the potential at vertex $i$). Then the current is
$$I_e = \frac{V_e}{R_e} = \frac{U_v-U_u}{R_e}.$$
The "source" and "sink" vertices have additional in and out currents, respectively.

## Kirchhoff's Matrix
Let $K = (K_{ij})$ which is the weighted Laplacian Matrix with edge weights $1/R_e$:
- $K_{ij}$ is $-\frac{1}{R_e}$ if $i \neq j$ is connected by an edge
- $K_{ij}$ is $\sum_{e\text{ incident to }i} \frac{1}{R_e}$ if $i=j$

Set the potential of the last vertex (the one hooked up to the negative side of the battery) to be 0. This makes potentials uniquely defined.

Turns out:
$$\tilde{K} \begin{bmatrix}U_1\\\vdots\\U_{n-1}\end{bmatrix} = \begin{bmatrix}I_{in}\\0\\\vdots\\0\end{bmatrix}.$$
We can normalize either the voltage of the battery or the current across the battery.

## Cramer's rule things
Cramer's rule takes in a system
$$Ax = b$$
and solves for $x$ by subbing out columns in $A$ for $B$ and calculating determinants.

By Cramer's rule:
$$U_1 = \frac{\tilde{\tilde{K}}}{\det \tilde{K}}$$

**Theorem.** The effective resistance
$$R_{in}(G)$$
is equal to
$$\frac{\sum_{2-\text{forests of G}} \prod_{e \in F} \frac{1}{R_e}}{\sum_{T\text{ spanning tree of }G} \prod_{e\in T} \frac{1}{R_e}}$$
