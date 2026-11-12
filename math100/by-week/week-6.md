## Equivalence Relations
---
A relation $\sim$ on set $A$ is an equivalence relation if $\sim$ is *reflexive, symmetric, and transitive*. Recall the definitions for these properties to find that, $\forall a,b,c \in A$:
$$ \begin{align}\sim \text{ on } A \text{ is an equivalence relation} \iff &(a\sim a)  \\ &\land  (a\sim b \implies b \sim a) \\ &\land \ (a \sim b \land b \sim c \implies a \sim c)\end{align}$$
Then for an equivalence relation $\sim$ on set $A$, $(\sim, A)$, an *equivalence class* of an element $x \in A$, $[x]$ is defined as:
$$ [x] = \set{y \in A\mid y \sim x}$$
where $x$ is the *representative* of the class $[x]$. So the equivalence class of element $x$ can be thought of as the set of all other elements in $A$ that relate to $x$ (or vice versa by symmetry). This is an important classification because each equivalence class divides $A$ as a subset in such a way that makes each equivalence class unique. That is, the set of equivalence classes of $A$ *partitions* $A$ (explained below).

Consider the equivalence relation $\equiv(\mod 3)$ on $\mathbb{Z}$. A possible output of performing $x\mod3$ is $0$, so consider the equivalence class of $0$:
$$\begin{align}
[0] &= \set{x \in \mathbb{Z} \mid x \equiv 0(\mod3)} \\
&=\set{x \in \mathbb{Z} \mid 3|(x-0)} \\
&=\set{x\in \mathbb{Z} \mid 3|x} \\
&=\set{x \in \mathbb{Z} \mid x = 3m \text{ for some }m \in \mathbb{Z}}
\end{align}$$
That is, $[0]$ contains all of the integer multiples of $3$, which is intuitive when considering that $x \equiv 0 (\mod 3)$ asks us which values of $x$ have remainder $0$ when divided by $3$. But notice that this set could also be rewritten as $[3]$ (but also $[6], [9]$, etc.) which would have elements $x \equiv 3 ( \mod 3)$. So we can equivalently call this equivalence class $[\text{Integers that have remainder 0 when divided by 3}]$.

So for some equivalence class, we can say that there exists some shared *property* amongst elements of that class and write it as $[\text{property}]$ even though $\text{property} \not\in A$.

In the previous example, we showed that there are an infinite number of degenerate cases that can be grouped into the single property "integers that have remainder 0 when divided by 3." So a task is to find all of the equivalence classes while ignoring the degenerate cases. For the previous example, once we've identified that the property that we are classifying on has something to do with the remainder when an integer is divided by $3$, we can speculate that the remaining properties must just be the possible remainders when an integer is divided by 3. For $3$, there are only 3 options: $\mod3 = 0, 1, 2$.  We can explicitly see this:
$$ \frac{0}{3} = 0 R0 \\ \ \\ \frac{1}{3} = 0 R1 \\ \ \\ \frac{2}{3} = 0R2 \\ \ \\ \frac{3}{3} = 0R0 \\ \ \\ \vdots$$
Note that the remainder values repeat after $0,1,2$. So the three equivalence classes for the equivalence relation $\equiv (\mod 3)$ on $\mathbb{Z}$ are $[0], [1]$, and $[2]$, or $[\text{Integers that have remainder 0 when divided by 3}], [\text{Integers that have remainder 1 when divided by 3}]$, and $[\text{Integers that have remainder 2 when divided by 3}]$.

Also, for set $A$ with equivalence relation $\sim$, we have:
$$[x] = [y] \iff x\sim y \\ \ \\ [x] \cap [y] = \emptyset \iff x \not\sim y$$
### Partitions
A collection of subsets of $A$ partition $A$ *iff* they are mutually disjoint and their union is the original set $A$. 

From the above statements, we know that the intersection of two equivalence classes is empty only if their representatives are not related by equivalence relation $\sim$. This ensures that the equivalence classes of $A$ are each mutually disjoint because if $x \sim y$, then $x \in [y]$, but $x \sim x$ by reflexivity, which would imply that the intersection would not be empty.

 This fact, paired with the fact that $\forall x \in A, x \in [x]$ by transitivity, proves that for any number of equivalence classes defined on $A$, their collection forms a partition of $A$:
$$\bigcup_{i \in \Lambda} [x]_i = A \ \text{ and } [x]_i \cap [x]_j = \emptyset \ \text{ for } i \ne j$$
### Well-Definedness
Define the set of equivalence classes of $A$ as $A/\sim$. 
>[!note]- this is all wrong and im too lazy to fix it
Now (naively) define functions $f: A \to B$ and $\hat{f} : A/\sim \to B$. A natural construction of such a function is $\hat{f}([x]) = \hat{f}(x)$, that is, applying the function to an equivalence class outputs, consistently, the function of its representative. Notice that equivalence class $[x]$ can be represented by any of the elements $y \in [x]$ while still representing the same equivalence class. So, for equivalence class $[x] = [y]$, we want $\hat{f}([x]) = \hat{f}([y]) = \hat{f}(x)$. That is, we want the output to consistently be one unique value independent of the choice of representative. Notice that this only works if $\hat{f}(y) = \hat{f}(z) \ \forall y,z \in [x]$.  If this is the case, we say that $\hat{f}$ is *well-defined*. 
Maybe a more intuitive way to put this is that a well-defined function should output the same value for elements that are "equivalent" or share some property that causes them to be in the same equivalence class. For example, the equivalence class of fractions that reduce to $0.5$ is
$[\frac{1}{2}] = \set{\frac{1}{2}, \frac{2}{4}, \ldots, \frac{64}{128}, \frac{12}{24}}$. If we had some function that had $g([\frac{1}{2}]) = 2$ but $g([\frac{2}{4}]) = 8$, then $g$ would not be well-defined because it would output two different values for two *equivalent* inputs. 
Here lies a subtlety that hasn't been previously explained but, this restriction on $\hat{f}: A/\sim \to B$ implies the more standard definition for a well-defined function which is that, function $h$ must map *every* element in input set $C$ to a *unique* element in $D$.  So when constructing $\hat{f}([x]) = \hat{f}(x)$, the function that we instantiate isn't necessarily a function by construction; it is merely a relation before it is confirmed that the rule holds consistently ($\hat{f}(y) = \hat{f}(z) \ \forall y,z \in [x]$). But more generally, what this alternative definition guarantees is that if $A$ is some complex set, and we're able to simplify it down into its equivalence classes (distinct, nonoverlapping properties), and also show that a function $\hat{f}$ outputs the same value regardless of representative, then we can conclude $\hat{f}$ is a well-defined function on $A \to B$. So, $\hat{f}: A/\sim \to B$ need not be a function whose function value is the function applied to the representative. In fact, $\hat{f}$ is well-defined if it just meets the condition that it maps *every* equivalence class of $A$ to a unique value of another arbitrary set $B$.
However, this standard definition means that checking whether functions are well-defined entails finding exceptions to the restrictions (*every input is mapped* and is *mapped to only one output*). By partitioning the input set into mutually distinct properties that completely compose $A$ and checking if $\hat{f}([x]) = \hat{f}(x)$ for each of these properties, the well-definedness of $\hat{f}$ on the set of equivalence classes transits to the original function $f: A \to B$ without having to manually check for the existence and uniqueness of inputs and outputs.

___