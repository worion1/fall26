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

### Single-Indexed Infinite Operations


### Nested Sequences of Sets (special case)



### Doubled-Indexed Infinite Operations
What if we choose $x = 2$? Then if we choose $k=1$ and $n=2$, we have the interval (1/2, 3/2), which doesn't include 2, but that's okay because we're supposed to union all of the intervals for every possible k in Z, thus there will exist an interval such as n=2 and k is some integer such that 2 is in that interval, or more broadly, unioning all of these possible intervals gives us a radius around k of 1/n (1/2 here) for all integers k. Thus if we choose n=2 and look for x=2, we can just say k=2, and then we've found the interval that 2 is kept in since the -1/n and +1/n just gives us a radius around the chosen x or k. Thus any choice of x will be kept. But if we choose a noninteger, then we can always find a large enough n such that the radius, or the "gaps around the chosen integer k", get smaller and smaller such that the decimal we are looking for is not kept in the interval for all possible values of n. As n goes to infinity, 1/n actually approaches 0, so if one proposes an a noninteger x, we can always claim that when n is approaching infinity, the interval will simply be an integer, and we won't find their noninteger.

## Proving Set Equality
___


## Set Exponentiation
___
