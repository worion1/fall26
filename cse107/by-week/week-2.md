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
$S_X=\set{x : p_X(x) >0}$. For example, if $X$ records the face value of a rolled die ($X(\omega) = \omega$), then the support of $X$ is $S_X = \set{1,2,3,4,5,6}$. Notice here that a value $x = 1.5$ would be assigned a probability of $0$ by the PMF and thus not belong to $S_X$.

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
## Cumulative Distribution Function (CDF)
---
The definition of the CDF is very similar to the PMF except that, instead of returning the probability of a random variable $X$ at a single real value $x$, it returns a cumulative probability of $X$ up to a real value $t$:
$$F_X(t) = P(X \le t),\space t \in \mathbb{R}$$
Then if $X$ is a discrete random variable, the only contributions to the cumulative probability come from jumps/steps, or values in the support of $X$ with $p_X(x) >0$. For any choice of $t$, we can choose a subset of $S_X$ to pass into the PMF and sum:
$$F_X(t) = \sum_{x \in S_X,\space x \le t} p_X(x)$$
While the PMF handles the space between $x$ values belonging to $S_X$ by outputting $0$, the CDF maintains a running total of the probability up to $t$ and, therefore, must be piecewise defined where $F_X(t) =0$ before the first discrete contribution and be nondecreasing.

Consider the following table listing the probabilities in the PMF of a discrete random variable $X$:

| $x$      | 0             | 1             | 2             | 3             |
| -------- | ------------- | ------------- | ------------- | ------------- |
| $p_X(x)$ | $\frac{1}{4}$ | $\frac{1}{4}$ | $\frac{1}{4}$ | $\frac{1}{4}$ |
It should be clear that $F_X(0)=P(X \le 0)\equiv P(X=0)=p_X(0)=\frac{1}{4}$ since $0$ is the only value in the interval $(-\infty, 0]$ that contributes to the probability of $X \le 0$. Likewise, if we are asked $F_X(1.5)=P(X \le 1.5)$, even though $1.5$ is not in the support of $X$, we simply imagine contributions of $0$ for the interval $(1,1.5)$ and keep moving backward toward nonzero contributions. Thus, $F_X(1.5)=\frac{2}{4}$.

We can actually plot this CDF by adhering to the piecewise definition and using the support values of $X$ to note where the "spikes", or nonzero probability contributions, occur.
![[Pasted image 20261009100033.png|center|475]]

### $P(X)$ Over a Finite & Half-Open Interval
If we want to find the probability of a random variable over a finite and half-open interval, specifically $a < X \le b$, we can use $P(a < X \le b) = F_X(b) - F_X(a)$. 

Note that we can rewrite the event $X \le b$ as a disjoint union: 
$$\set{X \le b} = \set{X \le a} \cup \set{a < X \le b}$$
Noting that this is indeed a disjoint union, we can invoke the additivity axiom:
$$ P(X \le b) = P(X \le a) + P(a < X \le b)$$
Recall that $P(X \le k)$ for some $k \in \mathbb{R}$ is precisely the definition of the CDF:
$$F_X(b) = F_X(a) + P(a < X \le b)$$
Finally we have,
$$P(a < X \le b) = F_X(b) - F_X(a)$$
## Bernoulli Trials
---
The introduction of Bernoulli trials and the Bernoulli distribution serves as motivation for the Binomial Distribution. 

We first define a Bernoulli trial as a binary random variable, capable of outputting the value $1$ if the outcome of an experiment is a "success" and the value $0$ if it is a "failure" (or other analogous terms). Thus, the $i$th Bernoulli trial is denoted:
$$I_i = \begin{cases} 1,& \text{success}, \\ 0,& \text{failure}.\end{cases}$$
If each $i$th trial has probability $p$ of occurring (that is, $P(A_i) = p$ because a trial is an indicator), then we know that, for each trial, its probability follows the a PMF:
$$p_{I_i}(u) = pI_{\set{u=1}} + (1-p)I_{\set{u=0}}$$
where $u$ is a value that $I_i$ takes on, indicating either success (1) or failure (0). In this case, we say that Bernoulli trial $I_i$ follows a Bernoulli distribution with success parameter $p$, or: $I_i \sim \text{Bern}(p)$.
## Binomial Distribution
___
If we assume these trials to be *mutually independent* (each trial is independent of *every* other trial), we can use the multiplication rule to write:
$$P(I_1=i_i, \ldots, I_n=i_n) = p_{I_1} (i_1) \cdot \ldots \cdot p_{I_n}(i_n)=\prod^n_{j=1}P(I_j = i_j),\space\space i_j \in \set{0,1}$$
Consider the specific pattern of four Bernoulli trails shown below:
![[Pasted image 20261012143920.png]]
where $S$ denotes "success" and $F$ denotes "failure", with respective probabilities $p$ and $1-p$.

Applying the multiplication rule to these (assumed) mutually independent trails, we find:
$$p(1-p)\cdot p(1-p)=p^2(1-p)^2$$
Generalizing this to a specific pattern of $n$ Bernoulli trials containing $k$ successes:
$$\text{pattern probability } = p^k(1-p)^{n-k}$$
Now let $X$ be a random variable that counts the number successes ($k$) in $n$ Bernoulli trials. If we want to define a PMF for $X$, observe the statement $P(X=k)$. Here, we are asking for the probability that there are $k$ successes in a given pattern. It may seem intuitive to say $P(X=k) = \text{pattern probability}$ for some pattern with $k$ successes, however, because $k$ successes can appear in a variety of arrangements of $n$ trials (e.g. $SFS \ne FSS$ despite $k=2$), we need to count the total number of arrangements. We can do this by imagining that we are assigning $k$ successes to $n$ trials awaiting an assignment (where any trial not assigned a success is instead assigned a failure). More importantly, realize that we are choosing *position indices*, that is, we are choosing $k$ position indices from $n$ total. Thus, we know that we can count the total number ways to get $k$ successes as $\binom{n}{k}$. Since the total number of successes/failures for any of these $\binom{n}{k}$ mutually independent patterns is identical, their pattern probabilities are also identical. Invoking the additivity axiom tells us that the probability of getting $k$ successes is just the sum of all of the $\binom{n}{k}$ patterns and repeated addition of the same term is simply multiplication, thus we have:
$$p_X(k) = \binom{n}{k} p^k (1-p)^{n-k} I_{\set{k \in \set{0, \ldots, n}}}$$
where the indicator is used to ensure $k$ is a valid selection of number of successes.
___