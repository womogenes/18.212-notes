Notation for ranked posets:
1. $\rho: P \rightarrow \{0, 1, \dots, \ell\}$
2. $P_i = \{a \in P \mid \rho(a) = i\}$ (set of elements with rank $i$)
3. $r_i = |P_i|$ ("rank values")

**Definition.** $P$ is
1. **rank symmetric** if $r_i = r_{\ell-i}$ for all $i$.
2. **unimodal** if rank numbers increase up to some value and then decrease
3. **Sperner** if the maximum size of an antichain equals exactly the maximum rank number

**Crucial definition.** A **symmetric chain decomposition** (SCD) of $P$ is a decomposition of $P$ into a disjoint union of saturated chains
$$P = C_1 \cup C_2 \cup \dots \cup C_n$$
such that for all $i$, $C_i$ starts at rank $j$ and ends at rank $\ell-j$.

**Lemma**. If $P$ has a symmetric chain decomposition, then it is rank-symmetric, unimodal, **and Sperner**.

*Proof.* The first two are easy to see because we can visualize it as a collection of vertical lines that are centered vertically.

Every antichain intersects every chain at most once. This means that the size of any antichain is at most $m$, where $m = r_{\ell/2}$ is the size of middle rank (due to unimodality). The middle rank also happens to be the biggest (because unimodality), which proves Sperner-ness.

## Boolean lattices
$B_n$ is the set of binary $n$-tuples, ordered by covering.

**Theorem.** $B_n$ is Sperner.

**Theorem.** (stronger than the previous one, 1948) $B_n$ has a symmetric chain decomposition.

*Proof.* The rank numbers (sizes of ranks) are the binomial coefficients $\binom{n}{i}$.
[[this is not a proof ??]]

**Corollary.** There exists an order-preserving, injective maps
$$\binom{[n]}{i} \rightarrow \binom{[n]}{i+1}$$
for all $i < n/2$ ... ?

## Product of posets
Define
$$P \times Q = \{ (p, q) \mid p \in P, q \in Q\}$$
with $(p, q) \le (p', q')$ if and only if $p \le_P p'$ and $q \le_Q q'$.

Equivalently, the covering relation (which uniquely defines a poset for finite posets!) is defined by the covering relations in $P$ and $Q$, i.e.
$$(p, q) \lessdot (p, q')\text{ where }q \lessdot q'$$
and vice versa are the only covering relations.

**Definition.** The $n$-chain is $[n] = \{1 < 2 < \dots < n\}$. If you do $[3] \times [4]$, you get a lattice.

If you do $([2] \times [2]) \times[ 2]$, you get a cube. In particular, $B_n = [2] \times [2] \times \dots \times [2]$, where $[2]$ is repeated $n$ times.

**Theorem.** Any product of chains
$$[n_1] \times [n_2] \times \dots \times [n_k]$$
has a symmetric chain decomposition.

*Proof.* By induction ??

**Lemma.** If both $P$ and $Q$ have symmetric chain decompositions, then so does $P \times Q$.

*Proof.* Decompose $P$ and $Q$ as
$$P = C_1 \cup C_2 \cup \dots \cup C_a$$
and
$$Q = D_1 \cup D_2 \cup \dots \cup D_b.$$
Pick a SCD for each product $C_i \times D_j$ (it's isomorphic to $[|C_i|] \times [|D_j|]$).

**Dilworth's theorem.** The maximal number of elements in an anti-chain in $P$ equals the minimum number of chains needed to cover all elements of $P$.

^ This follows from the observation that any antichain intersects any chain at most once.

**Mirsky's theorem.** Same claim, but switch the words "chain" and "antichain."