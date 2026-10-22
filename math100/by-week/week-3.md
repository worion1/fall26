## Principle of Mathematical Induction
---
A collection of $n \in \mathbb{N}$ statements $\set{P(n)}_{n \in \mathbb{N}}$ is indexed by writing $P(n)$. The Principle of Mathematical Induction (PMI) is an implication statement about such a collection that states that, if the first and $n$th statement being true implies that the $(n+1)$th statement is true, then the statement is true for any $m$ in the collection, thus proving the statement true for all considered cases.
	*Principle of Mathematical Induction (PMI)* $$\left() P(1) \land \forall n \in \mathbb{N}\left[P(n) \implies P(n+1)\right]\right) \implies\forall m \in \mathbb{N} \space \space P(m) $$
This principle is telling us that if we can prove the first implication to be a true statement, then we can know that $P$ is true for any $m$. Thus, our goal using induction is to prove that the first implication statement is true. Using the method of direct proof, we can break down proof by induction into three steps:
1) Base Case: Prove that $P(1)$ is true by plugging $n=1$ into $P$.
2) Inductive Step: Assume that $P(n)$ (inductive hypothesis) is true and invoke the inductive hypothesis to show that $P(n+1)$ is true.
3) Conclusion: Write "This concludes the inductive step" and state that $P(m)$ is true for all $m \in \mathbb{N}$ by method of inductive proof.
## Well-Ordering Principle
___
The Well-Ordering Principle (WOP) states that if we have a nonempty set $S$ that is a subset of the naturals $\mathbb{N}$, then that set has a smallest element. To use the Well-Ordering Principle as a proof method, the non-empty set $S$ is usually defined as a subset of $\mathbb{N}$ (thus its elements are all positive integers) such that for each element in $S$, its corresponding indexed statement $P(n)$ is false. The WOP is then invoked to state that $S$ contains some smallest element $l$, and then show that this leads to a contradiction.
### Steps for Proof by WOP
1) Let $S$ be a subset of $\mathbb{N}$ of counterexamples of the statement $P(n)$ 
   e.g. $S=\set{n\in \mathbb{N} \mid P(n) \text{ is false}}$.
2) For contradiction, state that $S$ must be nonempty i.e. $S \ne \emptyset$.
3) Invoke the WOP to state that $S$ has a least element $l$.
4) Check the base case $P(1)$, show that $l\ne1$ and thus $l>1 \implies (l-1) \in \mathbb{N}$.
5) State that $(l-1) \not\in S$ because $l$ is the least element, then assert that $P(l-1)$ is true.
6) Now start with the LHS of $P(l)$ and use $P(l-1)$ being true to deduce that $P(l)$ is true.
7) Since $P(l)$, $l \notin S$ but also from step 3, $l \in S$. Since the assumption that lead to the contradiction was that $S \ne \emptyset$, then $S = \emptyset$.
8) Conclude $\forall n \in \mathbb{N}$, $P(n)$. 
### WOP $\implies$ PMI
To show that the WOP implies the PMI, we can follow these steps exactly. First, recall the definition of the PMI: $$\left[ P(1) \land P(n) \implies P(n+1)\right] \implies P(m) \space\space\forall m \in \mathbb{N}$$
Note that saying that $P(n)$ implies $P(n+1)$ is equivalent to saying that $P(n-1)$ implies $P(n)$ if we just shift the indices over (if they are valid in the sense that we are not indexing outside of our index set). 

Now define $S$:
$$S = \set{\underbrace{n \mid P(n) \text{ is false}}_{\text{counterexamples of  PMI}}} \subset \mathbb{N}$$
Assume $P(1)$ and $\forall n \in \mathbb{N}, P(n) \implies P(n+1)$. For contradiction, assume $S \ne \emptyset$ such that there exists counterexamples to the PMI. 

Then invoke the WOP by letting $l$ be the smallest element of $S$ such that $l\ne 1$ because $P(1)$ is true by the hypothesis of the PMI. Because $l$ is the smallest element of $S$, it is trivial to say that $(l-1) \not\in S$. But, $P(l-1) \implies P(l)$, so $P(l)$ must be true, so $l \not\in S$. But also $l \in S$, so we have found a contradiction. Thus $S \ne \emptyset$ must be false, meaning $S = \emptyset$. 

Since we stated that $S$ is the set of counterexamples of the PMI and deduced that $S$ is empty, this proves that $P(n)$ must be true for all $n \in \mathbb{N}$, proving the PMI. $\square$
___