Before break: Cayley's Formula
- \# of labeled trees on $n$ vertices is $n^{n-2}$
- Proof by induction on elementary observations about trees and polynomials

Today: 2 bijective proofs
- Prufer coding, 1918
- Egecioglu-Remmed bijection, 1986

## Proof #1
Bijection between
- labeled trees $T$ on $n$ vertices
- set of all maps from $[n]$ to $[n]$ such that $f(1) = 1$ and $f(n) = n$.

Example: $n=15$
- Take $1$ and $n$ and find the shortest path between them. Lay the nodes in between on a line, and draw the rest of the tree stemming out from this line.
- Motivation: we've talked about equidistribution of statistics on permutations.
- We want to convert the tree into something that looks like a "generalized permutation"
- Direct all edges of $T$ towards vertex $n$
- Let $P$ be the path from 1 to n.
	- Find all records (left-to-right maxima) in $P$
	- e.g. if $P$ is $1, 7, 3, 8, 13, 9, 10, 15$
	- then the records are 7, 8, 13, and 15, because they are the "maximum so far" if we look left-to-right.
- Remove all edges in front of the records. So the edges going to 7, 8, 13, and 15 are removed.
	- Then make disjoint cycles from the remaining edges. Singletons go back to themselves, while other chains get looped back.
	- Reattach the nodes not on $P$.
	- The remaining graph tells us what $f$ is. It literally defines it.

ULTIMATELY, what we get is a set of cycles, with optional smaller trees attached to each cycle.
- Inverse mapping: make the graph from $f$, mark the maximum element in each connected component, link them together in increasing order, break the edge going to each maximum component. Boom we have a tree!
- (we also must ignore edge direction at the end)

We can deduce stronger results. If we count the number of records in the path from 1 to n, it is equal to the number of maps $f$ such that you get that number of connected components.
- Or something like this

## Proof #2
Prufer codes.

We define the Prufer code of a tree. For any tree $T$, let code(T) be a sequence of numbers
$$(c_1, c_2, \dots, c_{n-2}) \in [n]^{n-2}$$
where each $c_i$ is an integer from 1 to n.

To construct the Prufer code of a labeled tree:
1. Find the leaf $\ell$ with least degree
2. Note the vertex $c$ that it's adjacent to
3. Record $c$ in the code
4. Erase the edge $(\ell, c)$
5. Repeat this step ${n-2}$ times.

To go from a code back to a tree, observe:
- Indices that don't appear in the code are the leaves
- Let $C$ be the code
- Let $L$ be the set $\{1, 2, 3, \dots, n\}$
- Loop;
	- Find the lowest element in $L$ that doesn't appear in $C$
	- Remove it from $L$, and erase the next element of $C$
- This gives you all the edges, which reconstructs the tree.