## Functions
___
A relation $R$ from set $X$ to set $Y$ is a function if and only if it satisfies these properties:
$$
1) \space \ \ \forall x \in X, \exists y \in Y \text{ s.t. } (x,y) \in R \\
\space \\
2) \space \ \ (x,y) \in R \land (x,z) \in R \implies y=z 
$$
When speaking of functions, we call $X$ the *domain* ($\text{Dom}(f)$) and $Y$ the *codomain* ($\text{Codom}(f)$) of the function $f$. So, a relation is a function if and only if every element in the domain is mapped, and those elements are mapped to only one element in the codomain. It follows from this that if an element in the domain is mapped to two elements in the codomain, that those elements in the codomain must be the same element. Also, the set of elements that are *actually* mapped by $f$ is called the range of $f$, or $\text{Rng}(f)$.

From this we know that a function is defined by the specific sets that it performs a mapping between, and it's rule in *how* it does that mapping. In other words, we formally a declare a function as
$$ f: A \to B, \ y=f(x)$$
So two functions with the same rule need not be the same function if their domain or codomain aren't equal (or more obviously, if their rules are not identical). In fact, two functions $f$ and $g$ are equal if and only if they have the same domain, codomain, and rule.
$$\text{Dom}(f) = \text{Dom}(g) \land \text{Codom}(f) = \text{Codom}(g) \land f(x) = g(x) \ \forall x \in \text{Dom}(f) \implies f=g$$
### Images
For any function $f: A \to B$, it is also true that $f: P(A) \to P(B)$. For $C \subseteq A$, this means that $C \in P(A)$. Then, the *image* of $C$ under $f$ is defined as
$$f(C) = \set{f(c) \mid c \in C}$$
Reading this out we have that for any subset $C$ of the domain of $f$, $f(C)$ is the set of all of the values when $f$ is applied to each element in $C$. Essentially, the image of a subset of $\text{Codom}(f)$ just gives us the range for that subset. It follows then that the image of the entire domain of $f$ is simply $\text{Rng}(f)$.
### Preimages
For any function $f: A \to B$ with $D \subseteq B$ such that $D \in P(B)$, the *preimage* of $D$ under $f$ is defined as
$$f^{-1}(D)=\set{x\in A \mid f(x) \in D}$$
That is, the preimage of any subset of $\text{Codom}(f)$ is the set of values in $\text{Dom}(f)$ whose function value is an element of $D$. In other words, the preimage of $D$ just tells us which values in the domain map to the values in $D$. Also NOTE that this is **not the inverse** of $f$, also usually denoted as $f^{-1}$. It is true that every function has a preimage, but not every function has an inverse.

### Properties of Images and Preimages of Collections of Sets
Given a collection of sets $\set{A_\lambda}_{\lambda \in \Lambda}$, each of the following are true:
$$f^{-1}\left(\bigcup_{\lambda \in \Lambda}A_{\lambda}\right) = \bigcup_{\lambda \in \Lambda}f^{-1}(A_{\lambda})$$
$$f^{-1}\left(\bigcap_{\lambda \in \Lambda}A_{\lambda}\right) = \bigcap_{\lambda \in \Lambda}f^{-1}(A_{\lambda})$$
$$f^{-1}(A_{\lambda}^c)=(f^{-1}(A_{\lambda}))^c$$
$$f\left(\bigcup_{\lambda \in \Lambda}A_{\lambda}\right) = \bigcup_{\lambda \in \Lambda}f(A_{\lambda})$$
$$f\left(\bigcap_{\lambda \in \Lambda}A_{\lambda}\right) \subseteq \bigcap_{\lambda \in \Lambda}f(A_{\lambda})$$

### Function Properties
For any function $f: A \to B$, $f$ may or may not have the following properties:

<u>Injective</u> *(one-to-one)*
$$\begin{align}f \text{ is injective } &\iff \forall a,b \in A, a\ne b \implies f(a) \ne f(b) \\ &\iff \forall a,b \in A, f(a) =f(b) \implies a=b \\ &\iff (A = B=\mathbb{R}) \land f \text{ passes the horizontal line test} \end{align}$$
Note that the second definition is simply the converse of the first. $f$ being injective basically means that unique things in the domain map to unique things in the codomain. If $f$ maps $a$ to $f(a)$, then $a$ is *the only* element in $A$ that maps to $f(a)$. So if two elements map to the same value, they must be equal.

<u>Surjective</u> *(onto)*$$\begin{align}f\text{ is surjective} &\iff \forall b \in B, \exists a \in A \text{ s.t. } f(a)=b \\ &\iff \text{Codom}(f) = \text{Rng}(f) \\ &\iff \forall b \in B, f^{-1}(\set{b}) \ne \emptyset\end{align}$$The first definition says that for *every* element in the codomain, there *must* be an element in the domain such that $a$ is mapped to $b$ by $f$. What this means is that everything is covered in the codomain, which means that the codomain is equal to the range. The last definition is a little more subtle. It says that for every element in the codomain, the preimage of the singleton containing that element is not empty. Using the definition of the preimage, we can break the definition down
$$\forall b \in B, \set{x\in A, f(x) \in \set{b}} \ne \emptyset$$
So if we take each element in the codomain and turn it into a singleton, then there must be some element in the domain whose function value is in that singleton and is therefore the element $b$.
<u>Bijective</u>
$$f \text{ is bijective} \iff f \text{ is injective and surjective} $$

### Inverse Functions
The inverse of a function, denoted $f^{-1}$, is the function that "undoes" whatever $f$ does. The following are true statements about function inverses for some function $f: A \to B$
$$\exists f^{-1}(x) \land \left(f^{-1}: \text{Rng}(f) \to A\right)\iff f \text{ is injective}$$
$$f \text{ is bijective} \iff f^{-1}: B \to A$$
So if $f$ is only injective, then an inverse exists only for a restricted domain. But if $f$ is also surjective, the inverse exists as a mapping from $\text{Codom}(f)$ to $\text{Dom}(f)$.

#### Function Composition
The  composition of two functions, denoted $(h \circ k)(x)$, is a function itself and is written
$$(h\circ k)(x) = h(k(x))$$
You evaluate the inner function first using the input $x$, and then feed the output to the outer function.

Also if $f^{-1}$ exists, then:
$$ f(f^{-1}(x)) :=f \circ f^{-1}: B\to B := \text{Id}_B \\ f^{-1}(f(x)):=f^{-1} \circ f: A \to A:=\text{Id}_A$$
So what follows is that if $f \circ g = \text{Id}_B$ and $g \circ f = \text{Id}_A$, then $g$ must be the inverse function $f^{-1}$
$$f\circ g = \text{Id}_B \land g \circ f = \text{Id}_A \implies g = f^{-1}$$
From this, it follows from the definition of bijectivity that
$$f(g(x)) :=f \circ g = \text{Id}_B \implies f \text{ is surjective} \\ g(f(x)):=g \circ f = \text{Id}_A \implies f \text{ is injective}$$
___