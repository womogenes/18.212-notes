If $p(n)$ is the # of partitions of $n$,
$$\sum_{n \ge 0} p(n)\, q^n = \frac{1}{1-q} \cdot \frac{1}{1-q^2} \cdot \frac{1}{1-q^3} \cdots$$
This is apparent because every unit of $q^n$ comes from some partition of $n$, each of which comes from a unique selection of terms (one from each fraction). e.g.
$$2 + 2 + 3 + 5$$
comes from selecting the $(q^2)^2$ term, the $(q^3)$ term, and the $(q^5)$ term.

In 1748, Euler proved that the number of partitions of $n$ with all **odd** parts equals the number of partitions of $n$ with all **distinct** parts.

*Proof.* Their generating functions are equal !! the odd one goes
$$\frac1{1-q} \cdot \frac1{1-q^3} \cdot \frac{1}{1-q^5}\cdots$$
and the distinct one goes
$$(1+q)(1+q^2)(1+q^3)\cdots$$
The odd one can be multiplied by the even one on top and bottom to get
$$\frac{(1-q^2)(1-q^4)(1-q^6)\cdots}{(1-q)(1-q^2)(1-q^3)(1-q^4)\cdots}$$
Difference of squares! For every
$$1-q^i$$
in the denominator, there's a
$$1-q^{2i}$$
in the numerator. They cancel to give $1+q^i$. So the whole product is
$$(1+q)(1+q^2)(1+q^3)\cdots$$
## Fibonacci ??
The first few partition numbers are
$$1, 1, 2, 3, 4, 7.$$
The first few Fibonacci numbers are
$$1, 1, 2, 3, 5, 8.$$
Conjecture:
$$p(n)=p(n-1)+p(n-2)-p(n-5)-p(n-7)$$
This works for $n<12$, but we need to add corrective terms in the future as well...
$$
\begin{align*}
p(n) = p(n-1) + p(n-2) - p(n-5) - p(-7) + p(n-12)\,+\\ p(n-15) - p(n-22) - p(n-26)...
\end{align*}
$$
The gaps vary in size. Hm. The signs also alternate + + - -.

Something surprising:
$$\prod_{k \ge 1} (1-q^k) = 1 - q - q^2 + q^5 + q^7 - q^{12} - q^{15} + \dots$$
If we take every other number (1, 5, 12, 22, ...), we get the pentagonal numbers. The formula for the pentagonal numbers is
$$\frac{k(3k-1)}{2}.$$
## Euler's pentagonal numbers theorem
$$\prod_{k \ge 1} (1-q^k) = \sum_{k\in\mathbb{Z}} (-1)^k \cdot q^{k(3k-1)/2}.$$
First conjectured in 1741, proved in 1750.

*Proof.* Due to Franklin, using the "involution principle."

If we had
$$\prod_{k \ge 0} (1+q^k),$$
we'd get the generating function for the number of partitions of $n$ with distinct parts.

But we don't, so we actually get
$$ \prod_{k\ge1} (1-q^k) = \sum_{\lambda\text{ part. with distinct parts}} (-1)^{\text{\# parts in }\lambda} q^{|\lambda|}.$$
This is called an "involution" ?

We map a partition to another partition with the same number of boxes, but with either one more or one fewer row.
- Take $A$, which is the longest "diagonal" in the top-right (longest prefix of $\lambda$ that is stepping down 1 each time)
- Take $B$, which is last row
- If $|A| < |B|$, stick the boxes at $A$ down below $B$
- If $|A| \ge |B|$, stick $B$ to the right of $A$.
This creates an involution, which pairs up opposite-signed terms on the right-hand side of the sum.

EXCEPT when $a$ and $b$ intersect!
- When $|A| = |B|$ or $|A| = |B|-1$, we get an edge case, which produces the pentagonal numbers :O