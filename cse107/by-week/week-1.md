## Sample Spaces and Events
--- 
The result of an experiment is an outcome $\omega$, a single element represented as an integer, string, etc. When a 6-sided die is rolled, an outcome is guaranteed to be an integer in the range of 1 through 6. The set of all possible outcomes of which a single outcome is "picked" from is defined as the *sample space* $\Omega$ for a given experiment. Any subset of $\Omega$ (including $\Omega$ itself) is an event set $E$. An event $E$ occurs if and only if the outcome of an experiment satisfies $\omega \in E$.
![[Pasted image 20260928151535.png|center|257]]
Consider two events $A = \set{1,3,5}$ and $B = \set{2,4,6}$. These events occur when an outcome of a die roll is odd or even respectively. Note that $A$ and $B$ share no common elements (outcomes). Recall from basic set theory that the intersection $\cap$ operation between two sets results in a set of common elements between those two sets. We write $A \cap B = \emptyset$ to mean that intersecting the sets $A$ and $B$ results in the empty set $\emptyset$, representing the fact that events $A$ and $B$ share no common outcomes. In other words, we say that $A$ and $B$ are disjoint events. In the case of a die roll, this makes sense because a single outcome (an integer between 1 and 6) cannot be both even and odd at the same time. $A$ and $B$ are mutually exclusive events.
## Probability Rules
___
The probability of an event $A$ is denoted $P(A)$ and is constructed from three axioms that serve to normalize and regulate its output.
1. $P(A) \ge 0$ --- negative probabilities are not practical to real-world applications. 
2. $P(\Omega) = 1$ --- ensures that an outcome is guaranteed for an experiment.
3. $E_1, \ldots, E_m$ pairwise disjoint $\implies P\left(\bigcup^m_{i=1}E_i\right) = \sum^m_{i=1}P(E_i)$ --- where pairwise disjoint means that the outcomes of each event are specific to that event, i.e. no two events share a common outcome. This is called the additivity axiom.
There are several rules that come from these axioms when combining them with basic set theory operations. Below is a list of those rules and their derivations.
### Complement Rule
For any arbitrary set $A \subset \Omega$, the complement of that set is denoted as $A^c$ and defined as the set of outcomes not in $A$ but in $\Omega$. Naturally, we can express the union of $A$ and its complement as $\Omega = A \cup A^c$ and note that this is a disjoint union by how we defined the complement. Applying the probability function to both sides we get $P(\Omega) = P(A \cup A^c)$. Then invoking the second and third axioms get us:
$$\begin{aligned}1 &= P(A) + P(A^c)\\ P(A) = 1 - P(A^c) &\iff P(A^c) = 1-P(A) \end{aligned}$$
### Inclusion-Exclusion Principle
Note that the additivity axiom only applies for disjoint events. Consider $E_1 = \set{1,2}$ and $E_2 =\set{2,3}$. If the outcome "2" contributes $0.1$ to the probability of either $E_1$ or $E_2$ occurring, then computing the probability of the union as the sum of the probability of each event would be double counting the $0.1$ probability component.

Assume $A$ and $B$ are two events. We can imagine them in a Venn diagram as two separate regions and a third middle region serving as the event/set $A \cap B$. Each region contains points representing outcomes that only belong to that event.
$$\begin{align}
A \cup B &= A \cup (B \setminus  (A \cap B)) \\
P(A \cup B) &= P(A \cup ( B \setminus (A \cap B))) \\
P(A \cup B) &= P(A) + P(B \setminus (A \cap B)) \\
\end{align}$$
I will explain the first three lines before continuing on with simplifying the scary last term. We start by defining the union of events $A$ and $B$ as the union of $A$ with everything that's in $B$ but not in both events. This is still consistent with the concept of union because even if we included the outcomes in $A \cap B$, those extra outcomes would disappear because sets do not allow repetition of elements. Then we apply the probability function to both sides of the equation. Note that since we excluded the overlap between the events in the first step, we now have a disjoint union in the RHS. Thus the third step follows naturally according to the additivity axiom.
$$\begin{aligned}
B &= (A \cap B) \cup (B \setminus (A \cap B)) \\ 
P(B) &= P((A \cap B) \cup (B \setminus (A \cap B))) \\
P(B) &= P(A \cap B) + P(B \setminus (A \cap B)) \\
P(B \setminus (A \cap B)) &= P(B) - P(A\cap B)
\end{aligned}$$
Now we've rewritten the scary last term as something more manageable. The first step in doing so is to rewrite $B$ as the union of the overlap between $A$ and $B$ (that middle region) and the region that only contains $B$. This is because if $A \cap B$ has any outcomes, they are outcomes that also belong to $B$, so combining them with $B$ itself doesn't do much since duplicate outcomes are ignored. Then we apply the probability function to both sides and invoke the additivity axiom since the two events are disjoint (clearly so; the right event is literally the set $B$ MINUS the left event). Then we rearrange the equation to get a nice substitution to continue our work in the previous set of equations.
$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$
## Counting and Probability
___
Consider the sample space of rolling a fair 6-sided die: $\Omega = \set{1,2,3,4,5,6}$. What if we wanted to compute the probability of rolling any of those six numbers? If we define the event of rolling any number as $A$, then our intuition would correctly guide us to concluding that $P(A) = \frac{1}{6}$. This intuition however is dependent on the fact that we know that the die is fair, that is, the likelihood of rolling one number is the same as rolling any of the other numbers. If this is the case, we treat the problem less in terms of probability and more in terms of proportions. There are six possible outcomes and each outcome is equally likely as the others, so of course there would be a one in six chance of rolling a specific number. But what if there were many more outcomes in $\Omega$ and what if $A$ was much more complicated? More importantly, what if the experiment tells us that we need to exclude a number from the sample space after rolling it, or that the order by which we receive outcomes doesn't matter? We are still given the advantage of equal likelihood, but now the task becomes *counting* the size of $A$ and comparing it to the size of $\Omega$. 
### Permutations with Replacement
We start with the same example of the fair 6-sided die. Assume that the experiment tells us to roll three dice and record the results as an ordered tuple $(x_1, x_2, x_3)$. Starting with the first roll, there are six numbers that could possibly occur. On the second roll, there are still six numbers that could occur. The same goes for the third roll. If we just focus on the first two elements of the tuple and fix $x_1 = 1$, then we can see that there are six scenarios that could follow:
$$(1, 1, x_3), (1, 2, x_3), (1, 3, x_3), (1, 4, x_3), (1, 5, x_3), (1, 6, x_3)$$
But notice that we can also fix $x_2$ or $x_3$ and change the others as well. Thus, each outcome in roll $i$ propagates 6 possible arrangements in the next roll and for the first two rolls, we have $6 + 6 + 6 + 6 + 6 + 6 = 6*6$ possible arrangements. Since we have a 3-tuple though, we get $6*6*6$ possible arrangements.

Therefore, when making $k$-ordered choices (or draws) from $n$ objects (like numbers) with replacement (the same numbers are available after each draw), then the total number of permutations is:

$$ n \cdot n \cdot \ldots \cdot n = n^k$$
### Permutations without Replacement
The next formula for counting comes very naturally following this one. Suppose that we are drawing 3 cards from a deck of 52 cards. It is intuitive that, in this scenario, drawing a card means removing it from the pool of possible cards to draw for the successive draw.  Therefore, for a single run of the experiment, the possible choices for each draw from the deck decreases $52 \to 51 \to 50$. Then, applying the reasoning that was discussed earlier on how the arrangements propagate, we can conclude that the total number of permutations in this scenario is just $52 * 51 * 50$. This should seem reminiscent of factorials if you are familiar with them, something like multiplying a number by itself minus one. Noticing that it does stop at some point tells us that it isn't exactly a mere factorial. This truncated factorial is just a pattern that occurs when you divide a factorial by some lesser factorial, giving you the decreasing product until (lesser number + 1).
$$(n)_k = n \cdot (n-1) \cdot \ldots \cdot (n-k + 1)= \frac{n!}{(n-k)!}, \space k \le n$$
### Combinations
For some $k$-element set, the number of ways to reorder its elements is $k!$. This can be shown by taking a set (event), and rewriting it in every possible ordering as ordered tuples.
$$A=\set{a,b,c} \to \begin{aligned}(a,b,c), (a,c,b), (b,a,c),\\(b,c,a), (c,a,b), (c,b,a)\end{aligned}$$
In this example there are $|A|! = 3! = 6$ possible orderings.
If the order of the outcome of an experiment does not matter, then we say that it is a *combination*. Abstractly, a combination is the same as the permutation, except that order does not matter. So to reduce the count for combinations (since there are $(k! - 1)$ extra counts in permutations), we simply find the permutations and then divide by $k!$.
$$\binom{n}{k} = \frac{(n)_k}{k!} = \frac{n!}{k!(n-k)!}$$
Say that we are drawing 2 balls from a bag of 4 red balls and 6 blue balls where order does not matter. So a sample outcome looks like $\set{B, R}$. It is apparent that in this situation, choosing a ball from the bag also means removing that ball from the bag for the rest of the experiment. To count the total possible ways to draw or "choose" 2 balls from a bag of 10 total balls, we compute $\binom{10}{2} = \frac{10!}{2!(8!)} = 45$. If we define the event $A$ as choosing exactly two red balls, then there are $\binom{4}{2} = 6$ favorable outcomes. Thus, assuming uniform probability, $P(A) = \frac{6}{45}$.
### Probability Problem Solving
What if instead of $A$ being defined as something that we can count easily and directly with one of the counting formulas, it was something like "at least 3 red" or we were instead choosing many more balls from a bag. It may be clear that trying to count the favorable outcomes of "at least 3 red" when an outcome is an unordered sequence of 8 balls is difficult. To count the number of favorable outcomes, we would need to count the number of ways to draw exactly 3 red balls, then exactly 4 red balls, and so on.

An approach that resolves this tedious solution method is to use the complement rule to compute $P(A)$ indirectly.
___
1. Count all possible outcomes ($|\Omega|$) using one of the counting formulas.
2. Define and count the number of favorable outcomes in the complement set $A^c$.
3. Use uniform probability $P(A^c) = \frac{|A^c|}{|\Omega|}$.
4. Invoke the complement rule $P(A) = 1 - P(A^c)$.

## Conditional Probability
___
We can also compute the probability of an event $A$ occurring *given* an event $B$ has occurred. This is denoted $P(A | B)$ where "$|$" means "given". Event $B$ is also called the condition in this case, such that, any outcomes that we consider for $A$ must first meet the condition of $B$. Before $B$ occurs, the sample space for $A$ to be defined on (or "live in") is simply $\Omega$. Once we are consider $A$ *given* $B$, $B$ itself becomes the reduced sample space for $A$. For example, if we are asked the question "What is the probability that a rolled die is a 2 ($A$) given that it is even ($B$)", then the sample space to consider for $A$ is precisely $B$. Another way to put this is that $B$ gives us some extra information and restricts the elements of the sample space to those that satisfy its definition. Formally, conditional probability is given by:
$$\begin{aligned}P(A|B) &= \frac{P(A \cap B)}{P(B)},\text{ for } P(B) >0,\\  P(A|B) &= \frac{|A\cap B|}{|B|} \text{ if probability is uniform.} \end{aligned} $$
The numerator is $P(A \cap B)$ because after $B$ reduces the sample space, the only time $A$ will occur on that reduce space is if it also occurs with $B$, so we think of $A$ "and" $B$. If only $A$ occurs but not $B$, we are ignoring the condition, so the only sets in the new space are $B$ and $A \cap B$. In some sense, $B$ becomes the new sample space, but if $B$ is defined as a subset of $\Omega$ (as all events are), then $P(B) \le 1$. So when $B$ becomes the new space, we must renormalize the probability by dividing by $P(B)$. 
### Multiplication Rule (Conditional Probability)
We can rearrange the formula for conditional probability to get the multiplication rule:
$$ P(A \cap B) = P(A|B)P(B)=P(B |A)P(A), \text{ for}\space P(B) > 0$$
### Law of Total Probability
Before discussing the law of total probability, we first define a partition of the sample space $\Omega$ as follows:
$$\text{Subsets } B_1, \ldots, B_m \text{ partition } \Omega \iff B_i \cap B_j = \emptyset \text{ for } i \ne j \text{ and } B_1 \cup \ldots \cup B_m = \Omega$$
In other words, the subsets that partition the sample space must be pairwise disjoint and must also complete the sample space in the sense that every element in the sample space is covered by exactly one of the subsets.

Now assume that $B_1, B_2, B_3$ form a partition of $\Omega$. Consider event $A$ defined on this partition. Then we can write $A$ as a disjoint union of the intersection of $A$ and each subset in the partition:
$$A = (A \cap B_1) \cup (A \cap B_2) \cup (A \cap B_3)$$
We can reason this to be true by imagining a sample space cut into non-overlapping regions $B_i$. Then we superimpose a circle $A$ onto these regions and see that $A$ is now divided into non-overlapping regions where it joins with all of the $B_i$. To reconstruct $A$, we just take the union of all of these pieces of $A$, which are $A \cap B_1$. Applying the probability function to both sides and invoking the additivity axiom gets us
$$\begin{aligned}P(A) &= P((A \cap B_1) \cup (A \cap B_2) \cup (A \cap B_3)) \\ P(A) &= P(A \cap B_1) + P(A \cap B_2) + P(A \cap B_3)\end{aligned}$$
We can also rewrite this using the multiplication rule
$$P(A) = P(A|B_1)P(B_1) + P(A|B_2)P(B_2) + P(A|B_3)P(B_3)$$
Generalizing this to an $m$ sized partition, we have
$$P(A) = \sum^m_{i=1} P(A \cap B_i) = \sum^m_{i=1} P(A|B_i)P(B_i)$$
where $P(B_i) > 0$ for all $i$.

It is important to realize the utility of this law in situations where events such as $A$ are defined over a partition. If we imagine a tree structure for an outcome of an experiment, we see that there is a different probability for each outcome $A \cap B_i$ and, more importantly, a different probability for $A$ given each $B_i$ as a condition (visualized by the probability associated with moving from node $B_i$ to node $A$).
### Bayes' Theorem
This famous theorem follows naturally from substituting the multiplication rule and law of total probability into the definition of conditional probability,
$$P(B_j | A) = \frac{P(A \cap B_j)}{P(A)} = \frac{P(B_j)P(A|B_j)}{\sum^m_{i=1}P(A|B_i)P(B_i)}$$
where $B_1, \ldots, B_m$ must be strictly positive and form a partition of $\Omega$

Notice that the main utility of this theorem is to be able to work backwards from an event defined on a subset to that subset. In other words, $A$ might be the event "flight has been delayed" and the subsets that partition the sample space may be facts about the weather e.g. "sunny", "raining", "storm". Asking for the probability of a flight being delayed given that it is sunny out is intuitive, and denoted as the usual $P(A|B_{sunny})$. On the other hand, if we're given that the flight is delayed, it may seem less intuitive to be able to describe the probability that an individual weather is at fault, i.e. $P(B_{sunny} | A)$. 

We can further reason through this theorem by looking at what the numerators and denominators are really saying. The numerator is saying "What is the probability of a flight being delayed and it being sunny?", while the denominator is saying "How likely is the flight to be delayed under any weather?". Together they say "What is the probability of a flight being delayed and it being sunny out of all the delayed flight scenarios under any weather?"

---

