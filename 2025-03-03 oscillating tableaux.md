**Definition.** Young's Lattice $\mathbb{Y}$ is a(n infinite) poset on Young diagrams where
$$\lambda \lessdot \mu$$
if we can obtain $\mu$ by adding a box to $\lambda$.

**Claim.** Saturated chains (chains that go up without skipping any steps) from the empty Young diagram to $\lambda$ correspond to Standard Young Tableaux (where you fill in all the numbers) for $\lambda$.

*Proof.* Since each step up involves adding a box, we can just add numbers 1, 2, 3, ... in order.

**Definition.** $\mathbb{R}[\mathbb{Y}]$ is the linear space of **formal linear combinations** of Young diagrams. 

Define two **linear operators** $U$ and $D$ acting on $\mathbb{R}[\mathbb Y]$ to be
$$U(a \lambda + \mu b) = a U(\lambda) + b U(\mu).$$
With
$$U: \lambda \mapsto \sum_{\mu \mid \mu \gtrdot \lambda} \mu$$
where $\mu$ is obtained from $\lambda$ by adding a box, and
$$D: \lambda \mapsto \sum_{\mu \mid \mu\lessdot \lambda} \mu,$$
where $\mu$ is obtained from $\lambda$ by removing a box.

**Notice:**
$$U^n(\emptyset) = \sum_{\lambda \vdash n} f_\lambda \cdot \lambda$$
because this gives coefficients to every element on the $n$th row of the Young Lattice, and the coefficient of $\lambda$ is the number of ways to get to $\lambda$. Also,
$$D^n(\lambda) = f_\lambda \cdot \emptyset.$$
So
$$D^n U^n (\emptyset) = \sum_{\lambda \vdash n} (f_\lambda)^2 \cdot \emptyset = n! \cdot \emptyset.$$
Recall: RSK bijection:
$${(P, Q) \mid P\&Q Z\text{ of same shape}}$$
maps to $S_n$.

**Crucial lemma.** $DU-UD = I_N$.