## Negation of Universal and Existential Quantifiers
___
When negating a statement with universal or existential quantifiers, you swap the quantifier and negate the rest of the statement e.g.
$$\neg(\exists a \in \mathbb{Z} \text{ s.t.}  2\nmid a) = \forall a \in \mathbb{Z}, 2 | a$$
We can show this rule to be true by expressing the quantifiers as "large" conjunctions or disjunctions and negating their terms.
$$\begin{align}\neg\left(\exists x \in \mathbb{N}, A\right) &= \neg\left(\bigvee_{x \in \mathbb{N}} A(x)\right) \\
&=\neg \left(A(1) \lor A(2) \lor \ldots \right) \\
&=\neg A(1) \land \neg A(2) \land \ldots  \\
&=\left( \bigwedge_{x \in \mathbb{N}}\neg A(x)\right) \\
&=\forall x \in \mathbb{N}, \neg A(x)



\end{align} $$
## Sequences of Sets 
___
Sequences of sets are sets indexed by other sets. Thus, a sequence of sets is simply a collection of sets, with each set having a corresponding index in the index set. Let $A$ be a set of indices (e.g. positive whole numbers $\mathbb{N}$) with elements $\alpha$ and let $B_\alpha$ be the sets indexed by $A$. Then we denote a single set as $\set{B_\alpha}_{\alpha \in A}$ or $\set{B_\alpha \mid \alpha \in A}$.
### Infinite Operations
Now we can speak of a possibly infinite collection of sets and, more importantly, define (possibly) infinite operations over such a collection. For example, what if we wanted to ask if a single element $x$ belonged to *any* of the $B_\alpha$ sets indexed by $A$? We would write:
$$x \in \left[\bigcup_{\alpha \in A} B_\alpha\right]=\bigvee_{\alpha \in A}(x \in B_\alpha) = \set{x \mid x \in B_\alpha \text{ for atleast one } \alpha \in A} = \set{x \mid \exists \alpha \in A, x \in B_\alpha}$$
Likewise, for asking whether an element belongs to an intersection over sets we write:
$$x \in \left[ \bigcap_{\alpha \in A}B_\alpha\right] = \bigwedge_{\alpha \in A} (x \in B_\alpha) = \set{x \mid x \in B_\alpha \text{ for all } \alpha \in A} = \set{x \mid \forall \alpha \in A, x \in B_\alpha}$$
### Nested Sequences of Sets (special case)
If we have a sequence of sets so that each subsequent indexed set in the collection is contained by the previous, then it is nested. Consider the infinite sequence of sets $\set{A_n}_{n \in \mathbb{N}} = \left[0, \frac{1}{n}\right] \text{ for } n \in \mathbb{N}$. Writing out the first few terms of this sequence we have:
$$A_1 = [0, 1], A_2 = [0, \frac{1}{2}], A_3 = [0,\frac{1}{3}], \space \ldots$$
Notice that all of the possible real numbers that fit in $A_2$ are also in $A_1$. So $A_1 \supset A_2$. But notice that this is the case for all $n \in \mathbb{N}$. Thus $A_1 \supset A_2 \supset A_3 \ldots$.

Now if we ask if an element $x$ is in any $A_n$, we write:
$$x \in \bigcup_{n \in \mathbb{N}}A_n \equiv x \in \big([0,1] \cup [0, \frac{1}{2}] \cup [0, \frac{1}{3}]\cup \ldots \big) \equiv x \in [0,1]$$
We know that all of the real values (elements) in any interval indexed greater than $A_1$ are entirely contained in $A_1$, so if we're just looking for an element $x$ that belongs to *any* interval, that's the same as asking if $x$ is just in $A_1$. So if we are just performing the union over all $A_n$, we would just get the interval $[0,1]$.

Consider what happens when we write out the infinite intersection considering this information:
$$x \in \bigcap_{n \in \mathbb{N}}A_n \equiv x  \in \big([0,1] \cap [0, \frac{1}{2}] \cap [0, \frac{1}{3}]\cap \ldots [0,\frac{1}{n}]\big)$$
But notice that for any choice of $x$ such that $0 < x \le 1$, we can always find an $n$ such that $\frac{1}{n} < x$. So the only element that "survives" this intersection is the element (real value) $0$ included in the left argument of every interval:
$$x \in \bigcap_{n \in \mathbb{N}} A_n = {0}$$
### Doubled-Indexed Infinite Operations
A double-indexed collection of sets is indexed by two different sets of indices. For example, the sequence of sets $I_{n,k} =(k - \frac{1}{n}, k + \frac{1}{n})$ is indexed by two sets of indices: $A=\set{n \in \mathbb{N} \mid n \ge 2}$ and $B = \set{k \in \mathbb{Z}}$ (by definition of the problem). 

On such a collection we can define four operations. Before listing them, always remember that when dealing with these operations, we can always first consider that we are trying to find an element $x$ in these sets, and then use that to reason about what the resulting set should be. To reiterate, the task of finding the resulting set of any of these operations is closely related to trying to find which elements of $x$ "survive" the operations. For that reason, I will list the statements "$x \in \ldots$" and their equivalent forms using logical quantifiers.
	<u>Iterated Union</u> $$x\in \bigcup_{A} \bigcup_{B} I_{n,k} \equiv \set{x\mid \exists a \in A, \exists b \in B, x \in I_{n,k}}$$
	<u>Iterated Intersection</u> $$x \in \bigcap_A \bigcap_B I_{n,k}\equiv\set{x\mid\forall a\in A, \forall b \in B, x \in I_{n,k}}$$
	<u>Limit Supremum</u> $$x \in \bigcap_A \bigcup_B I_{n,k}\equiv\set{x \mid \forall a \in A, \exists b \in B : x \in I_{n,k}}$$
	<u>Limit Inferior</u> $$x \in \bigcup_A \bigcap_B I_{n,k}\equiv\set{x\mid\exists a \in A : \forall b \in B, x \in I_{n,k}}$$

___