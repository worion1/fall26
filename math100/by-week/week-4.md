## Principle of Strong Induction
___
The Principle of Strong Induction is given symbolically as follows:
$$\left(P(1) \land \left[\bigwedge^n_{k=1}P(k) \implies P(n+1) \right]\right) \implies \forall m \in \mathbb{N}, P(m)$$
The main difference between normal (or weak) induction and strong induction is the assumptions made in the inductive hypothesis. In normal induction, the induction hypothesis is that $P(n)$ is true while in strong induction, assuming the hypothesis assumes that $P(k)$ is true for all $1 \le k \le n$ after proving the base case $P(1)$.

Consider the Fibonacci sequence, defined by its recurrence relation:
$$F_n = F_{n-1} + F_{n-2}$$
Notice that the $n$th Fibonacci number depends on the two that come before it. If we wanted to prove $P(n)$ related to this recurrence relation, we would need to not only assume that $P(n)$ is true, but also $P(n-1)$.  Here lies a nuance about making these two assumptions, which is that, if we only proved $P(0)$ as our base case, and now we want to assume some arbitrary $P(k)$, let says $P(2)$, then since $P(2)$ relies on both $P(0)$ and $P(1)$, we still need to prove the $P(1)$ base case! Once this is done, we can ask whether or not we can assume $P(3)$ and the answer is yes because we just unlocked $P(2)$ by proving $P(0)$ and $P(1)$. This creates a domino effect that extends all the way to $P(k)$ for $1 \le k \le n$.
## Descending Chain Condition
___
The Descending Chain Condition (DCC) states that there are no infinite descending chains in the naturals, that is, every descending chain must converge to a constant or 0. 
$$n_1 > n_2 > n_3 > \ldots \implies \exists k \in \mathbb{N}, \underbrace{n_{k} = n_{k+1} = n_{k+1} = \ldots}_{\text{terms converge to a value}} \text{ or } \underbrace{n_k=0}_{\text{terms converge to 0}}$$
An example of where the DCC can be used is when trying to show that the Euclidean Algorithm terminates after performing the Division Algorithm an arbitrary number of times. For reference, this is the Division Algorithm:
$$ \forall a, b \in \mathbb{N}, \exists q, r \in \mathbb{N} \text{ s.t. } b=qa+r, \space r<a$$
In other words, if we $b$ by $a$, we expect two things in the result: a quotient ($q$) and a remainder ($r$) such that $\frac{b}{a} = q + \frac{r}{a}$. Since the remainder is the amount of $b$ left over after dividing wholly by $a$, multiplying both sides by $a$ gives us: $b = qa + r$.

Then the Euclidean Algorithm tells us to simply repeat the Division Algorithm by using the previous step's divisor ($a$) as the next step's dividend and its remainder ($r$) as the next step's divisor ($b$). We want to show that this will eventually leave us with a remainder of $0$. So, writing out the first few steps we have:
$$\begin{align} 
b&=q_1a +r_1, && r_1 < a \\
a&=q_2r_1 + r_2, && r_2 < r_1 \\
r_1 &= q_3r_2 + r_3, && r_3 < r_2 \\
\vdots && \vdots \\
r_{n-1} &= q_{n+1}r_n + r_{n+1}, && r_{n+1} < r_{n} \\
\vdots && \vdots
\end{align}$$
So we have a descending chain of remainder terms $a > r_1 > r_2> r_3> \ldots > r_n+1 > r_n > \ldots$ . In this case, they must converge to $0$ because of the strictly less than symbol, which tells us that the previous remainder term cannot be equal to the current, so we must stop at the last element in the naturals ($r \in \mathbb{N}$), which we'll say is $0$ here. Thus $r_n = 0$.

---
