### Definitions
- Statements and Statement Operations ✓
	- A statement has a *definite* truth value
	- Algebraic equations are statements if the variables are quantified (e.g. $\forall x \in \mathbb{R}, x+1=2$, which is definitely false)
- Sets and Set Operations ✓
	- $(A  \cup B)^c = A^c \cap B^c$
	- $(A \cap B)^c = A^c \cup B^c$
	- $A\setminus B =(A \cap B^c)$
	- $\cup, \cap$ are commutative.
	- $\cup, \cap$ are associative.
	- $\cup, \cap$ distribute like multiplication; $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$;
	   $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$.
	- $A \cup \emptyset = A$
	- $A \cap U = A$ 
	- $A \cup U = U$
	- $A \cap \emptyset = \emptyset$
	- $A \cup A = A$
	- $A \cap A = A$
	- $A \cup A^c = U$
	- $A \cap A^c = \emptyset$
	- $(A^c)^c = A$
	- $A^B = \set{f:B \to A \mid f \text{ is a function}}$
- Cardinality of Finite Sets ✓
	- $|A \times B| = |A||B|$
	- $|P(A)| = 2^{|A|}$
	- $|P(P(A) \times P(B))| = 2^{2^{|A| + |B|}}$
- Power Set ✓
	- $P(A) = \set{X \mid X \subseteq A}$
	- Don't forget the empty set $\emptyset$!!!!!!!!!!!!!!!!!!!!!
- Divisibility ✓
	- $a|b \iff \exists m \in \mathbb{Z}, b = ma$
- 4 Types of Induction ✓
	- PMI: $P(1) \land \left[P(n) \implies P(n+1)\right] \implies \forall m \in \mathbb{N}, P(m)$
	- PSI: $P(1) \land \left[\bigwedge_{k=1}^n P(k) \implies P(n+1) \right]\implies \forall m \in \mathbb{N}, P(m)$
	- WOP: $\forall S \subseteq \mathbb{N}, S \ne \emptyset, S \text{ has a least element.}$
	- DCC: 
		- No infinite descending chains exist in the naturals.
		- Every descending chain in the naturals must reach 0 or a constant;
		   $n_1\ge n_2\ge\ldots \implies (\exists k \in \mathbb{N}, n_k = 0 \text{ or } n_k=n_{k+1}=n_{k+2}=\ldots)$ 
- Relations & Properties ✓
	- A relation $R$ is a subset of the Cartesian product of two sets; $R \subseteq \set{(a,b) \in A \times B}$.
	- A relation $R$ on set $A$ is a subset of the Cartesian product of $A$ and itself; 
	  $R = \set{(a_1,a_2) \in A \times A}$.
	- If two elements $a_1, a_2 \in A$ are related by relation $R$ (i.e. $\exists (a_1,a_2) \in R$), we write $a_1 R a_2$.
	- For relation $R$ on set $A$ and $a,b,c \in A:
	  - $R \text{ is reflexive} \iff \forall a \in A, aRa$; every element in $A$ relates to itself by $R$. THIS IS THE ONLY PROPERTY WITH A UNIVERSAL CONDITION!!!
	
	  - $R \text{ is symmetric} \iff (aRa \implies bRa)$; if $a$ is related to $b$, then $b$ must be related to $a$ by $R$.
	
	  - $R \text{ is antisymmetric } \iff (aRb \land bRa \implies a=b)$; if $a$ and $b$ are symmetrically related, they must be the same element.
	
	  - $R \text{ is transitive } \iff (aRb \land bRc \implies aRc)$; if $a$ is related to $b$ and $b$ is related to $c$, $a$ must be related to $c$ by $R$.
- Partial Orders ✓
	- Reflexive, Antisymmetric, Transitive (RAT)
	- poset: $(S, R)$
	- For poset $(S,R), x,y \in S$:$$ x \text{ is the greatest element } \iff \forall y , x \ge y \\ \space \\ x \text { is the least element } \iff \forall y , x \le y \\ \space \\ x \text { is a maximal element } \iff \nexists y , \text{ s.t. } y>x. \\ \space \\ x \text { is a minimal element } \iff \nexists y, \text{ s.t. } y<x. $$
	  NOTE: For $x$ to be a greatest/least element it MUST be comparable to EVERY ELEMENT IN THE POSET!!!!!!!!!!!!!!!!!!
	  NOTE: It is vacuously true that if an element $x \in S$ is not related to any other element, then it is both minimal and maximal by those definitions.
	  NOTE: It is true that if a poset has strictly greater than 1 element, and there is at least one isolated element in that poset, then that poset has no greatest or least element.
	- $x \text{ is greatest } \implies x \text{ is maximal}$
	- $x \text { is least } \implies x \text{ is minimal }$
- Total/Linear Orders ✓
	- Partial Order + Trichotomy Law (total comparability)
	- Trichotomy Law: For $x,y \in S, x<y, x=y, \text{ or } x>y$ but only one.
	- For a toset $(S,R), x,y \in S$:$$ x \text { is greatest } \implies x \text{ is the unique maximal } \\  x \text { is least } \implies x \text{ is the unique minimal }$$

### Problems
- Completing Truth Tables ✓
- Writing Statements with Quantifiers ✓
- Negating Statements ✓
	- $\neg \forall x = \exists x$
	- $\neg \exists x = \forall x$
	- $\neg(a \le b) = a > b$
	- $\neg(a \ge b) = a<b$
- Intersections and Unions of Sets -> Arbitrary $\bigcap$ & $\bigcup$ of Indexed Sets?
		- For a given sequence of indexed sets, there are two mechanical workflows depending on how the sets are indexed:
			- $\set{A_n}_{n=1}^{\infty}$ is usually written interval notation (open, closed, or half-open) in HW 2.
				1) If the sequence is nested and decreasing, $\bigcup A_n = A_1= A_{\text{first index}}$.
				2) If the sequence is nested and increasing, $\bigcap A_n = A_{\text{first index}}$.
				3) Use the prior steps if applicable, then follow these steps if $A_n$ is nested:
						For $\bigcup A_n$, take the limit as $n \to \infty$. This gives you an interval with endpoints $(\lim f(n), \lim g(n))$. If $A_n$ is closed or half-closed, check that the limit boundary value is actually in the interval: $f(n) < \lim f(n) < g(n)$? If not, change the closed bracket to an open bracket.
					For $\bigcap A_n$, take the limit as $n \to \infty$. If $A_n$ is open, this will likely result in a empty interval $(a,a)$. If $f(n) < a < g(n)$, then $\bigcap A_n = {a}$, else it is the empty set. If $A_n$ is closed, no need to test the boundary value. 
				4) If $A_n$ is not nested:
					For $\bigcup A_n$, write out the first few terms of the union and infer the tail-end behavior of the endpoints. For $\bigcap A_n$, write out the first few terms of the intersection and either infer the tail-end behavior of the endpoints directly or evaluate the first few intersections to see if you get $\emptyset$. If you ever get $\emptyset$, then the entire intersection must be $\emptyset$.
			- $\set{A_k}_{k \in \Lambda}$ is followed by a definition of a sequence of sets, not intervals in HW 2.
				1) For $\bigcup A_k$, write out the first few terms of the union and infer what the resultant set is. Try to think about what indexing the set by $\Lambda$ really means when performing the union over all of the sets. For example, in problem 8c), we union over all $k \in \mathbb{Z}$ of $\set{k,k+1,\ldots}$, so by inspection this should just be $\mathbb{Z}$. For $\bigcap A_k$, write out the first few terms of the intersection and infer what the resultant set is. For the same problem, we notice that, for each subsequent increment in $k$, we lose the first element from the preceding set, so intersecting over all of $k$ gives us the empty set.
	- Double Arbitrary $\bigcap$ & $\bigcup$ of Indexed Sets ? <- On the exam???
		- Fix the outer indexing variable and apply the above-mentioned workflow to the inner operation, then infer what taking the outer operation results in.
- Proving Set Inclusions ✓
	- Let $x \in S$, use the property defining $x\in S$ to show that $x\in T$, conclude $S \subseteq T$.
	- $S=T \iff (S \subseteq T) \land (T \subseteq S)$
- Proof by Contrapositive ✓
	- Proof by contrapositive in an set inclusion proof
		- Proving set inclusion requires proving $S \subseteq T$ and $T \subseteq S$, which are two implicit conditional statements: $\forall s, s \in S \implies s \in T$ and $\forall t, t \in T \implies t \in S$, respectively. So invoke the contrapositive for each conditional you are trying to prove, and prove that contrapositive directly. Recall: $P \implies Q \equiv \neg Q \implies \neg P$.
	- Proof by contrapositive in a uniqueness proof
		- A uniqueness proof follows the form: $P(x) \land P(y) \implies x=y$, so naturally there is a way to prove this using the contrapositive by proving $x\ne y \implies \neg P(x) \lor \neg P(y)$.
- Standard Induction Proofs 
	- Sum = formula proof: reindex sum, invoke IH, show P(n+1)
	- $a | f(n)$ proof: $P(1)$->assume $a|f(n)$->write out $f(n+1)$->manipulate into $f(n) + \space$ something->can split divides operator by linearity property to focus on $a|\text{something}$->if you can, reduce $a|\text{something}$ into $2|n(n+1)$, which is true because $n(n+1)$ is guaranteed to be a multiple of an even number, which is divisible by 2. 
