Given a poset $P$, there is a something of $P$ which is the Hasse diagram but has all the comparable edges (not just the strict/saturated edges).

An **interval** of a poset is all the elements between two things (comparable to both)

What does the simplicial complex of Young's lattice look like?
- Let's take an interval $(\lambda_1, \lambda_2)$ of Young's lattice and look at what its simplicial complex looks like.

Question: how do the combinatorics of Young's lattice control the topology of its associated simplicial complex?

Let $\sigma \in \Delta$. Then $\langle \sigma \rangle$ is the subcomplex of all subsets of $\sigma$.
-A shelling order of the facets $F_1, F_2, \dots, F_n$ of $\Delta$ satisfies
$$\left(\cup_{i<j} \langle F_i \rangle\right) \cap \langle F_j \rangle$$
has to be (a) pure and (b) has dimension $|\dim(F_j)| - 1$.
- intuition: you add facets such that each new facet you add only intersects with the previous facets in a lower-dimension space.  ???

facets are maximal faces (things not contained in anything bigger)
- "pure" means all maximal faces are of the same dimension

Example: tetrahedron has three facets (the three triangles). Call them $F_1, F_2, F_3$. Then the claim is that
$$F_1, F_2, F_3$$
is a shelling order. "Pure" mean the intersection has one dimension less.

**Theorem.** A shellable complex is isomorphic to a set of spheres glued together.

**EL labeling.** New structure! Now we add labels to the edges. Given a subset of Young's lattice, label each edge with the row number of the box added.
- In each interval there is one increasing chain