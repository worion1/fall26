## Conditional Density Functions
___
A conditional density function with fixed $y$ is defined as:
$$ f_{X|Y}(x|y) = \begin{cases}\frac{f_{X,Y}(x,y)}{f_Y(y)}, & (x,y) \in S_{X,Y}, \\ 0, & \text{otherwise.} \end{cases} \ , \space \ f_Y(y) \ne 0$$
where this is a function of $x$ and is parameterized by $y$. 

The reverse is:
$$ f_{Y|X}(y|x) = \begin{cases}\frac{f_{X,Y}(x,y)}{f_X(x)}, & (x,y) \in S_{X,Y}, \\ 0, & \text{otherwise.} \end{cases} \ , \space \ f_X(x) \ne 0$$
Once obtaining these, we can evaluate them at specific values as follows:
$$ 
P(X \in A|Y=b) = \int_Af_{X|Y}(x|b)dx \\
P(Y \in A|X=b) = \int_Af_{Y|X}(y|b)dy
$$
where we are using the conditional density functions at some fixed value that we are *conditioning on*, then evaluating at some fixed value that we are *interested in*.

Something that also follows analogously from our knowledge of discrete conditional distributions is:
$$f_{X|Y}(x|y) = f_X(x) \text { or } f_{Y|X}(y|x) = f_Y(y) \iff X,Y \text{ independent} $$
### Conditional Expected Value
We can realize the formula for *conditional expected value* by thinking of it as the expected value of a conditional density function. That is, we have:
$$ \mathbb{E}[X|Y=y] = \int^\infty_{-\infty}xf_{X|Y}(x|y)dx$$
and likewise for the reverse:
$$\mathbb{E}[Y|X=x]= \int^\infty_{-\infty}yf_{Y|X}(y|x)dy$$
## Covariance and Variance 
___
Covariance is the measure of how two random variables change together. It's output ranges over
$(-\infty, \infty)$ and it is defined as:
$$\text{Cov}(X,Y) = \mathbb{E}[(X - \mu_X)(Y-\mu_Y)] \\ \space \\  \mu_X=\mathbb{E}[X],\ \mu_Y = \mathbb{E}[Y]$$
We can simply read this out as the "mean of the product of the deviations of $X$ and $Y$ from their respective means". So for a single datapoint, we have the following possibilities:

| $X$               | $Y$               | $\text{sign}(X-\mu_X)$ | $\text{sign}(Y-\mu_Y)$ | $\text{sign}((X-\mu_X)(Y-\mu_Y))$ |
| ----------------- | ----------------- | ---------------------- | ---------------------- | --------------------------------- |
| higher than usual | higher than usual | $+$                    | $+$                    | $+$                               |
| lower than usual  | lower than usual  | $-$                    | $-$                    | $+$                               |
| higher than usual | lower than usual  | $+$                    | $-$                    | $-$                               |
| lower than usual  | higher than usual | $-$                    | $+$                    | $-$                               |
So a single comparison of the deviations of $X$ and $Y$ from their respective mean is positive if they are both further away from their mean, and negative if one is further away while the other isn't. Taking the average over many comparisons tells us how the two random variables *change* together. That is, if $\text{Cov}(X,Y) > 0$, then most of the individual comparisons were positive, so $X$ and $Y$ change in the same way together. If $\text{Cov}(X,Y)<0$, most of the individual comparisons were negative, so $X$ and $Y$ change in the opposite way. If $\text{Cov}(X,Y) = 0$, then there is no pattern between how $X$ and $Y$ change together.

We can simplify the formula for covariance as:
$$\text{Cov}(X,Y) = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y]$$
and we have the LOTUS:
$$\mathbb{E}[g(X,Y)] = \underset{S_{X,Y}}{\iint} g(x,y)f_{X,Y}(x,y)dA$$
where $f_{X,Y}(x,y)$ is the joint PDF.

If $g(X,Y) = h(X)p(Y)$, then:
$$ X \perp Y \implies \mathbb{E}[h(X)p(Y)] = \mathbb{E}[h(X)] \mathbb{E}[p(Y)]$$ where $X \perp Y$ means "$X$ and $Y$ are independent."
### Correlation
Giving us a direct measure of the strength of the  linear relationship between $X,Y$, we define the correlation of $X$ and $Y$ as:
$$ \rho_{X,Y}=\frac{\text{Cov}(X,Y)}{\text{SD}(X)\text{SD}(Y)}$$
where $-1 \le \rho_{X,Y} \le 1$, $\rho$ is unitless.

If $\rho >0$, then $X \propto Y$; or $X$ and $Y$ change in the same direction; or $X$ and $Y$ are clustered closely along the line $y=mx + b$ where $m>0$.
If $\rho < 0$, then $X \propto -Y$; or $X$ and $Y$ change in the opposite direction; or $X$ and $Y$ are clustered closely along the line $y=mx + b$ where $m < 0$.
If $\rho=0$, then there is no linear relationship between $X$ and $Y$ and they are not clustered closely along a straight line (though $X$ and $Y$ could still have a non-linear relationship such as $X \propto Y^2$).
### Independence of $X$ and $Y$
The variance of a linear combination of $X$ and $Y$ is given by:
$$\text{Var}(aX +bY + c) = a^2\text{Var}(X) + b^2\text{Var}(Y) + 2ab\text{Cov}(X,Y) $$
Then, we have the following statements on the independence of $X,Y$:
$$X\perp Y \implies \text{Cov}(X,Y) = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y] = 0 \implies \rho_{X,Y} = 0 \\ \space \\ X \perp Y \implies \text{Var}(aX+bY+c) = a^2\text{Var}(X) + b^2 \text{Var}(Y)$$
### Sums & Sample Means
Let $X_1, X_2, \ldots, X_n$ be a collection of $n$ *independent* and *identically distributed* (*i.i.d*) random variables such that each has identical mean $\mu$ and identical variance $\sigma^2$. Then define $S_n$ as the sum of these random variables and $\bar{X}_n$ as the *sample mean*:
$$ S_n = \sum^n_{i=1}X_i \space \ , \space \ \bar{X}_n=\frac{S_n}{n} = \frac{1}{n}\sum^n_{i=1}X_i$$
Then we have:
$$ \mathbb{E}[S_n] = n\mu\space \ ,\space  \text{Var}(S_n)=n\sigma^2 \\ \space \\ \mathbb{E}[\bar{X}_n] = \mu\space \ , \space \text{Var}(\bar{X}_n)=\frac{\sigma^2}{n} \\ \space \\ \text{SD}(S_n) =\sqrt{n}\sigma\space \ , \space \text{SD}(\bar{X}_n) = \frac{\sigma}{\sqrt{n}}$$
___