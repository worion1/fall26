## Relations
___
A relation is a subset of the Cartesian product of two sets; $R := A \times B$. For example, if $A=\set{1,2,3}$ and $B = \set{a,b}$, then a relation could be defined as $R = \set{(1,a), (2,a), (3,b)}$.

However, we are more often concerned with relations that are defined on a single set. When we have $R:= A \times A$, we call this a *relation on A*. We see these types of relations when dealing with functions that map from $\mathbb{R}$ to $\mathbb{R}$, that is, $f : \mathbb{R} \mapsto \mathbb{R}$ is a relation on $\mathbb{R}$. For these types of relations, we define the following properties: 

>[!abstract] Properties of Relations
>For relation $R$ on set $A$,
><u>**Reflexive**</u>
>$$R \text{ is reflexive} \iff \forall a,b, \in A, aRa $$
>Every element in $A$ relates to itself by $R$.
><u>**Symmetric**</u>
>$$R \text{ is symmetric} \iff \forall a,b \in A, aRa \implies bRa$$
>If $a$ is related to $b$, then $b$ must be related to $a$ by $R$.
><u>**Antisymmetric**</u>
>$$ R \text{ is antisymmetric } \iff \forall a,b \in A, aRb \land bRa \implies a=b$$
>If $a$ and $b$ are symmetrically related, they must be the same element.
><u>**Transitive**</u>
>$$\forall a,b,c \in A, aRb \land bRc \implies aRc$$
>If $a$ is related to $b$ and $b$ is related to $c$, $a$ must be related to $c$ by $R$.

For each of these properties besides antisymmetric, you can think of one of the most common relations: $=$. It is trivial that, for element $a$ of any number set (e.g. $\mathbb{R}, \mathbb{N}, \mathbb{Z},$ etc.), we have $a=a$. Furthermore, we have that $a=b \implies b=a$ and $a=b \land b=c \implies a=c$.  
## Order Structures
___
There are three types of order structures: *partial orders*, *total/linear orders*, and *well-orders*.
### Partial Orders
A partial order for a set $S$ is a relation $R$ that is *reflexive*, *antisymmetric* and *transitive*. That is, when defining an ordering on a set, we pair it with a relation that meets the conditions. 

The most commonly seen partial order is the less than or equal relation $\le$ on the integers $\mathbb{Z}$, naturals $\mathbb{N}$, reals $\mathbb{R}$, etc. We can verify that this is a partial order on $\mathbb{Z}$ by expressing the relation properties explicitly. Is every integer $n$ less than or equal to itself? Yes, $n \le n$. If an integer $n$ is less than or equal to an integer $m$, and vice versa,  must they be the same integer? Yes, $n \le m \land m \le n \implies n=m$. Finally, if $n$ is less than or equal to $m$ and $m$ is less than or equal to $l$, must $n$ be less than or equal to $l$? Yes, $n \le m \land m \le l \implies n \le l$. 
### Total/Linear Orders
A linear order for a set $S$ is a relation $R$ if it is a *partial ordering* on $S$ and $S$ has the *trichotomy law*. 

>[!collorary] Trichotomy Law
>$$ \text{For } x,y, \in A, \text{ exactly one hold: } \\ x<y, \space, x=y, \space x>y$$

In other words, $R$ must be a partial ordering on $S$ and all elements of $S$ must be comparable by $R$ (totality). Again, this is most commonly seen as the relation $\le$ on a number set.

### Posets
The resulting object of a partial order on a set is a *partially-ordered set* (poset), denoted as $(S,R)$. For example, $(\mathcal{P}(\set{1,2,3}), \subset)$ is a poset. You may imagine that a poset is named such because if we were to try to draw connections between elements of set $S$ that represented two elements being related, not elements would be connected (unless of course the partial order is a total order). If each element in a poset is connected to each other element, then the structure collapses from a tree-like structure to a line (hence *linear order*) in which each element is related to every other element by $R$.

![[Pasted image 20261030104044.png]]

In any given poset (including *totally-ordered sets*; tosets), the elements can be *greatest*, *least*, *maximal*, or *minimal*.

>[!abstract] Greatest, Least, Maximal, Minimal Elements of Posets
>For any poset $(S,R)$, $x,y \in S$:
>$$ x \text{ is the greatest element } \iff \forall y , x \ge y \\ \space \\
>x \text { is the least element } \iff \forall y , x \le y \\ \space \\
>x \text { is a maximal element } \iff \nexists y , \text{ s.t. } y>x. \\ \space \\
>x \text { is a minimal element } \iff \nexists y, \text{ s.t. } y<x.
>$$

Note that in the definitions for the greatest and least element, it is implicit that these elements *must be* comparable to every other element in the poset. So, even if we see an element at the top or bottom of a tree, we cannot conclude that it is a greatest or least element if it is not connected to every other element (directly or by transitivity). 

In the above image representing the poset $(\mathcal{P}(\set{1,2,3}),\subset)$, we can say that $\set{1,2,3}$ is greatest and maximal and $\emptyset$ is least and minimal.  

Some other important identities are:
$$x \text{ is greatest } \implies x \text{ is maximal} \\ \space \\ x \text { is least } \implies x \text{ is minimal }$$ And, for a toset:
$$ x \text { is greatest } \implies x \text{ is the only maximal } \\ \space \\  x \text { is least } \implies x \text{ is the only minimal }$$

### Totally Ordered Subsets
Take a look at the poset $(\mathcal{P}(\set{1,2,3}),\subset)$ once again and notice that while not every set is a subset of every other set, there exists chains (subsets) of sets *within* the poset that are fully connected (that is, totally ordered by $\subset$). For example, the subset $\set{\emptyset, \set{1}, \set{1,2}, \set{1,2,3}}$ has each of its elements related to each other by transitivity: $\emptyset \subset \set{1} \subset \set{1,2} \subset \set{1,2,3}$. There are several other such subsets in this poset, including $\set{\emptyset, \set{1}, \set{1,2}}$. This chain would *not* be considered a *maximal totally ordered subset* (or maximal chain) because it is contained by the first chain that we mentioned. The other chain, however, *is* a maximal totally ordered subset because there are no other elements that can be added while keeping it totally ordered (in fact, there are no other elements to be added). 
![[Pasted image 20261030105411.png|573\center|550]]
### Well Orders
Set $S$ is well-ordered by $\le$ if every nonempty subset of $S$ has a least element e.g. $(\mathbb{N}, \le)$.