- A Young diagram is a graphical depiction of a partition $(\lambda_1, \lambda_2, \dots, \lambda_k)$ where row $i$ has $\lambda_i$ blocks in it, left-aligned
- A Young **tableaux** is a Young diagram with numbers in the boxes.

**Def.** A **Standard Young Tableaux** (SYT) of shape $\lambda$ (partition of $n$) is
- a way to fill boxes of $\lambda$ with 1, 2, .., $n$ without repetition
- such that the entries increase in rows and columns of the Young diagram

**Def.** $f_\lambda$ is the number of standard Young tableaux of shape $\lambda$.

**Prop.** The number of standard Young tableau of shape $(n, n)$, i.e. $f_{(n, n)}$, is the $n$th Catalan number.
- The Young diagram looks like two rows of $n$ blocks each.
- We construct a bijection with Dyck paths.
- A number in the top row means "go up" in the Dyck path
- A number in the bottom row means "go down" in the Dyck path
- We know that we never cross the $x$-axis because numbers must be increasing down each column
## The Hook Length Formula
Frame, Robinson, Thrall, 1953
- The **hook** at box $a$ is the set of boxes to the right or down of $a$ (including $a$ itself)
- The **hook length** of $a$ is the number of boxes in the hook at $a$
- $H(\lambda)$ is the product of hook lengths of **all** boxes in the diagram

For any partition $\lambda$ of $n$, the number of standard Young tableaux of $n$ is
$$f_\lambda = \frac{n!}{H(\lambda)}.$$
## Hook walk proof
"probabilistic proof"
- A **corner** of a young diagram is a block that has no blocks to the right or to the bottom
- In any SYT, the maximal entry must live in a corner

We know that:
$$f_\lambda = \sum_{c\text{ is a corner of}\lambda} f_{\lambda \setminus c}$$
Because casework / recursion / DP.

We can use induction to show that the hook length formula holds. The goal is to show that
$$\sum_{c\text{ is a corner of }\lambda} \frac{1}{n} \frac{H(\lambda)}{H(\lambda \setminus c)} = 1.$$
Because then we can use the inductive hypothesis for all $\lambda \setminus c$ and add things up.

**Hook walk:** start at a random box, take the hook, jump to a uniformly random box in the hook.
- Define the weight of a box $a$ as $\frac{1}{h(a) - 1}$.
- Define the weight of a path (hook walk) as the product of the weight of all the boxes in the path.
- **Observe:** if a hook walk ends in a corner, the entire walk must be contained in the rectangle to the left and up of the corner.

Lemma that we proved (using induction):
$$\sum_{P\text{ is a lattice path in rectangle}} \text{wt}(P) = \frac{1}{x_1 x_2 \dots x_k y_1 y_2 \dots y_k},$$
where $x_i$ is (hook length - 1) of box $i$ in the last row and $y_j$ is (hook length - 1) of box $j$ in the last column.

