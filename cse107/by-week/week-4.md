	## Expectation
___
Consider a discrete random variable $X$ with PMF $p_X(x) = P(X=x)$. So far, we have constructed discrete probability distributions that tell us about the likelihood of the event $\set{X = x}$ occurring for all real $x$. A question that naturally follows asks about what value $x$ would we *expect* to get if we ran the experiment many times. For example, if $X$ counts the heads on a fair coin toss, a common (yet trivially answered) question may be, "Do I expect to get heads more or tails more if I flipped many coins?" Obviously, since the odds are 50/50 for a fair coin toss, the expected value of heads over many iterations is simply 0.5 heads. Notice that 0.5 isn't actually a possible value that $X$ can take on, that is, $0.5 \not\in S_X$. This is perfectly fine, and nonetheless, this example gives us the right intuition as to how the expected value of a discrete random variable is actually computed. We took the probability of getting heads and multiplied it by the real number that getting heads corresponds to, ${X=1}$, and then took the probability of getting tails and multiplied by $X=0$, leaving us with $\mathbb{E}[X] = (0.5)(1) + (0.5)(0) = 0.5$. 

The expected value of a discrete random variable with a finite support and valid PMF is:
>[!abstract] Definition of $\mathbb{E}[X]$
$$\mathbb{E}[X]=\sum_{x\in S_X}xp_X(x)=\mu$$

Note that this sum resembles a weighted average, where each value in the support of $X$ is weighted by it's corresponding probability in the probability distribution. Also note that if $p_X(x)$ were simply $\frac{1}{N}$, where $N = |S_X|$, this would just be an arithmetic average. Thus, we can also describe the expected value as the *mean*, usually denoted as $\mu$. Now the fact that the expected value need not be a value contained by $S_X$ makes sense because we understand it to simply be a weighted average, not an expected observable outcome for a single run of an experiment.

Because $\mathbb{E}[X]$ is defined by the linear operator $\sum$, it shares it's linear properties, namely additivity ($\mathbb{E}[X+Y]=\mathbb{E}[X] + \mathbb{E}[Y]$), homogeneity ($\mathbb{E}[aX] = a\mathbb{E}[X]$). Furthermore, because $\mathbb{E}[X]$ is defined as a sum over the support of $X$, the operator retains the nonnegativity and monotonicity properties. Another property of the operator comes directly from it's definition as a sum that runs over $S_X$. Consider $X$ such that $S_X = \set{41}$, that is, the only value taken on by $X$ is $41$. Then, if we plug this into the sum definition of $\mathbb{E}[X]$, we simply get $41\cdot 1=41$ since the probability of an element of $S_X$ which only contains one element is simply $1$. Thus, $\mathbb{E}[c] = c$.     
## Variance
___
While the expected value of a random variable tells you the long term center or mean of a distribution, it doesn't necessarily describe how close the datapoints in that distribution are to this mean.
>[!example] Equal Means, Different Probabilities
>![[Pasted image 20261022201651.png]]

To fill this information gap, we introduce variance as a measure of the (probability weighted) average squared distance that the possible values taken by $X$ are from the expected value of it. 
$$ \sigma^2 = \text{Var}(X)=\mathbb{E}[(X-\mu)^2] = \sum_{x \in S_X}(x-\mu)^2p_X(x)$$
We square the argument of the expected value for two reasons. If we didn't square it, by linearity of $\mathbb{E}$, we would have:
$$\mathbb{E}[(X-\mu)] = \mathbb{E}[X] - \mathbb{E}[\mu] = \mathbb{E}[X] - \mu = \mathbb{E}[X] - \mathbb{E}[X] = 0$$
So we get no information. 

The other reason for squaring the argument is to weigh large deviations more. If an observed outcome is very far away from the mean with some attributed probability, squaring the difference in the sum corresponds to contributing *more* to the variance measure.

Because variance is measured in squared units, its interpretation is not always useful in direct analysis. So, we define the standard deviation as the square root of the variance, which is measured in original units:
$$\text{SD} = \sigma = \sqrt{\text{Var}(X)}$$
>[!tldr] Properties of Variance and Standard Deviation
$$\text{Var}(X)=\mathbb{E}[X^2] - (\mathbb{E}[X])^2 \\ \space \\ \text{Var}(aX + b)=a^2\text{Var}(X) \\ \space \\ \text{SD}(aX + b) = |a|\text{SD}(X)$$

## Joint Probability Distributions
---
A joint probability distribution is denoted $p_{X,Y}(x,y)$ and has the same properties as a univariate PMF. That is, the values are solely nonnegative and all sum to 1.
$$p_{X,Y}(x,y) \ge 0 \\ \space \\ \sum_X\sum_Y p_{X,Y}(x,y) = 1$$
We can think of the comma in the distribution argument as meaning "and" in that the joint probability distribution describes the likelihood of the intersection of events over a joint support: $p_{X,Y}(x,y) = P(\set{X=x} \cap \set{Y=y})$.

To find the probability of an event $A$ occurring, we compute the sum of the probabilities of each $(x,y)$ pair outcomes that belong to the event $A$. In other words, we go through each of the joint outcomes and only add those that satisfy the condition $A$ to the sum.
$$P((X,Y) \in A) = \sum_{(x,y) \in A}p_{X,Y}(x,y)$$
If we fix $X=x$, then the possible outcomes are limited to all of the pair outcomes that contain the fixed $x$, e.g. $(x, y_1), (x, y_2), (x, y_3),$ etc. Thus, the event $\set{X=x}$ is simply a union of all of these outcomes: $\set{X=x} = (x,y_1), (x,y_2), \ldots = \bigcup_y \set{X=x, Y=y}$. Note that each random variable can only take one value on at a time, so this is a disjoint union. So we have:
>[!abstract] Marginal Distributions
>$$\begin{align} P(\set{X=x}) &= P\left( \bigcup_y \set{X=x, Y=y}\right) \\ \space \\ 
\text{Fixed X: }\space p_X(x) = \sum_yp_{X,Y}(x,y) &\text{ or } \text{Fixed Y: } \space p_Y(y)=\sum_xp_{X,Y}(x,y)
\end{align}$$

These are called the *marginal distributions*, where we're able to recover the PMFs for some fixed $X$ or $Y$ by summing over the joint probabilities for some $X$ or $Y$. If we represent a joint distribution table as a table with cells $p_{X,Y}(x,y)$, this corresponds to selecting (fixing) a row or column, and then adding up all of the joint probabilities in that selection.
### Conditional Joint Probability Distributions
If we fix $X$ and have $P_X(x) > 0$, then we define conditional probability on $X$ of $Y$ as:
$$p_{Y\mid X} (y\mid x) = P(Y=y\mid X=x) = \frac{P_{X,y}(x,y)}{P_X(x)}$$
Recall that this formula is identical to conditional probability for events except that this can be defined as a distribution over all possible values of $y$.

We can use the multiplication rule to rewrite this as:
$$p_{X,Y}(x,y) = p_X(x)p_{Y \mid X}(y\mid x) = p_Y(y)p_{X\mid Y}(x\mid y)$$
We can use these to recover the marginal distributions for either $X$ or $Y$ as:
$$p_X(x) = \sum_{y \in S_Y} p_{X,Y}(x,y) = \sum_{y \in S_y}p_Y(y)p_{X\mid Y}(x\mid y) \\ p_Y(y)=\sum_{x \in S_X}p_{X,Y}(x,y)=\sum_{x\in S_x}p_X(x)p_{Y\mid X}(y \mid x)$$
Notice that this formula is identical to the Law of Total Probability.

Finally, we define independence of joint probability distributions as follows:
$$X,Y \text{ independent } \\ \Updownarrow\\\forall (x,y) \in (S_X\times S_Y), p_{X,Y}(x,y) = p_X(x)p_Y(y) \\ \Updownarrow\\ \forall x \in S_X, p_X(x)>0,\forall y \in S_Y, p_{Y\mid X}(y\mid x) = p_Y(y) \\ \Updownarrow \\ \forall y \in S_Y, p_Y(y)>0, \forall x \in S_x, p_{X\mid Y}(x\mid y) = p_X(x)$$
---



