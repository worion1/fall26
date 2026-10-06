## Statements & Logic Operators
___
We start the introduction to proofs by first learning about logic. Logic consists of using logical operators in conjunction with statements to create formal arguments that hold true for any selection of statement. Thus, logic is concerned less about the contents or meaning of a statement, or if the statement is actually true in the real world. Instead, logic cares about the validity of the structure and syntax of arguments.

Then, we can define a statement $P$ as a sentence or expression that has a definite truth value: True ($T)$ or False ($F$). A sentence such as "It is raining right now" is an example of a statement because it can be proven that it is actually raining or not. A non-example would be an equation (a mathematical sentence describing the equality of two expressions) such as $x+2=5$. Notice that the truth value of this equation is dependent on the value of $x$; it is true when $x=3$ but false if $x$ is any other number or, perhaps, the sentence "my dog is green". There is one caveat to such a counterexample which are algebraic tautologies, or identities, for which remain true or false for all possible inputs e.g. $x + x = 2x$ is true for all choices of $x \in \mathbb{R}$. 
### And & Or
Let $P,Q$ be statements. To form the statement $P$ "and" $Q$, we use the logical conjunction operator $\land$ and write $P \land Q$. The resulting statement $P \land Q$ must also have a definite truth value, but for two statements, there are four possible permutations for the truth values of $P$ and $Q$ respectively. To find the truth values of $P \land Q$ for each of these cases, we construct the following truth table:

| $P$ | $Q$ | $P \land Q$ |
| --- | --- | ----------- |
| $T$ | $T$ | $T$         |
| $T$ | $F$ | $F$         |
| $F$ | $T$ | $F$         |
| $F$ | $F$ | $F$         |
From the truth table, we can see that the logical conjunction's truth values accurately reflect the meaning of the word "and" in English, such that it is only a true statement if both $P$ and $Q$ are true. The question to why we consider $P \land Q$ a statement even though it's truth value changes may still linger. To address this, note that a statement does not have to have a fixed truth value, but a definite one when fixing the inputs of it. For example, when considering the case $P \land Q$, we are always fixing $P$ and $Q$ to either be true or false first.
