## Random Variables
---
Events are useful for describing experiments involving small sample spaces and concise outcomes. In the example of flipping two coins, the events that we can define on the sample space are solely descriptive of what we are looking for as outcomes e.g. $A = {\text{first flip is heads}}$. In order to quantify this system, we can instead define a *random variable* that maps specific outcomes to *real numbers*. So, instead of working with descriptive events and sets, we move to working with functions and output values. This allows us to apply everything that we know about real numbers to an probability instead of having to work strictly with set algebra.

A random variable is defined as:
$$X: \Omega \to \mathbb{R}$$
meaning that a random variable $X$ is actually a function whose domain is the sample space $\Omega$, and codomain is the reals. In other words, each outcome $\omega \in \Omega$ is mapped to a function value 
$X(\omega) \in \mathbb{R}$, i.e. $\omega \mapsto X(\omega)$.

We can define events using random variables with $\set{X = x}$ for some choice of $x \in \mathbb{R}$. For example, consider a single coin toss ($\Omega = \set{H,T}$) and $X$ records the number of heads. Then $\set{X = 1}$ is the event that the tossed coin is a head, or $A = \text{coin was heads}$. 
Formally,  $\set{X=1} = \set{\omega \in \Omega \mid X(\omega) = 1}$.
## Probability Mass Function (PMF)
___
The probability mass function (PMF) of random variable $X$ is given by:
$$p_X(x) = P(X = x)$$
where $x$ is a specific value taken by $X$. In plain words, this is simply a function that outputs the probability that the random variable is equal to some number $x$. 

The values of $x$ that result in a strictly positive $p_X$ belong to the *support* of $X$, defined as 
$S_X=\set{x : p_X(x) >0}$. For example, if $X$ records the the face value of a rolled die ($X(\omega) = \omega$), then the support of $X$ is $S_X = \set{1,2,3,4,5,6}$. Notice here that a value $x = 1.5$ would be assigned a probability of $0$ by the PMF and thus not belong to $S_X$.

Because $p_X$ is a probability function on $X$, it must retain properties of probability that we are familiar with:
$$p_X(x) \ge 0, \space \sum_{x \in S_X} p_X(x) = 1$$
where the former simply states that the probability of the random variable being equal to a value must be nonnegative and the latter states that the sum of all probabilities in the support of $X$ must be equal to $1$.

Because $p_X(x)$ assigns a probability to each of the values yielded by $X$, $p_X(x)$ characterizes a *probability distribution* of the range of $X$.
### Indicator (Random Variable)
An indicator is a piecewise random variable (function!) whose only outputs (out of all of the reals, remember) are: $1$ when outcome $\omega$ is in $A$ and $0$ otherwise. 
$$I_A(\omega) = \begin{cases} 1,&\omega \in A, \\ 0&\omega\not\in A \end{cases}$$
Also, $\set{I_A =1} = A$ and $\set{I_A = 0} = A^c$.

Indicators can also be used to implicitly define the support of $X$ when included as a factor of the PMF of $X$ e.g.
$$p_X(x) = \left(\frac{x}{10}\right) I_{x \in \set{1,2,3,4}} \\ \downarrow \\ p_X(x) >0 \iff I_{x \in \set{1,2,3,4}}=1 \iff x=1,2,3,4 \\ \downarrow \\ S_X = \set{1,2,3,4}$$
Here, the indicator is not a function of an outcome $\omega$, but of a real variable $x$. 
## Cumulative Distribution Function
---


