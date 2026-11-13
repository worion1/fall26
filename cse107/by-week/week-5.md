## Probability Density Functions
---
We now transition from using discrete random variables to using continuous random variables. The distinction between the two is that continuous random variables can take on an uncountably infinite number of values (e.g. $X \in \mathbb{R}$), whereas a discrete random variable takes on a finite or countably infinite number of values.

Directly from this definition, a few issues immediately arise. If continuous random variable $X$ is defined for an uncountably infinite number of values, and each point for which $X$ is defined (or is nonzero) must have an associated probability, each point's associated probability must be so small in order to satisfy the condition that the total probability must be $1$. In fact, the probability of $X$ taking on any specific value $x$ is precisely zero.

>[!NOTE]- tangent explanation
In other words, suppose that we have some butter that we wish to spread on a piece of toast. Imagine that we spread the butter on the piece of toast evenly and cut it into fourths. Then, each of the four parts of the toast have some butter on them. Suppose that we continue cutting until we have 100 parts of toast. It is still reasonable to say that each part of the toast has butter on it. But imagine what happens when we're considering if each atom of the toast has some butter on it, or some other number so unimaginably large. For the same amount of butter, it is unreasonable to conclude that each atom of toast has some butter on it because summing up all of the butter over all of the atoms of toast would probably not representative of the amount of butter that we spread over the toast initially since we're counting so many atoms.
We can also view this idea from a purely mathematical perspective. For example, consider a discrete random variable whose probability mass function is defined as $p_X(x) = \frac{1}{2^k}$ for $k \in \mathbb{N}$.  Then notice that there are an infinite number of values that $X$ takes on that have nonzero probabilities: $\frac{1}{2}, \frac{1}{4}, \frac{1}{8},\ldots$, yet the sum over all possible values of $k$ yields: $\sum_{k\in \mathbb{N}} \frac{1}{2^k} = 1$.
Suppose (though it is not technically possible) that we have a continuous random variable with PMF defined as $p_X(x) = \frac{1}{2^k}$ for $k \in [0,1]$. The amount of values in the interval $[0,1]$ is *uncountably infinite*, so the sum over all possible values of $k$ diverges to infinity: $\sum_{k \in [0,1]} \frac{1}{2^k} \text{ diverges}$, violating the condition for a valid probability measure. To reconcile this, we say that each value that $X$ takes on has point probability zero (in the same way that a single point of a piece of toast has zero butter on it), that is, $\forall x \in S_X, P(X=x) = 0$.

To get around this, we instead define a *probability density function* (PDF) denoted $f_X(x)$ to measure the probability density of continuous random variable $X$. Note that this function *does not measure the probability of* $X$, so it's range can be greater than $1$. When integrating over mass density we expect to get mass, so integrating over probability density gives us probability. Note that this reinforces the idea of zero point probability that was mentioned earlier. If we try to integrate this function to get $P(X = x)$, we integrate over a rectangle (for example) with zero width and height $f_X(x)$, yielding zero area and zero probability. Some properties of probability density functions are:
$$ 
\forall x \in \mathbb{R}, f_X(x) \ge 0 \\ \ \\ 
\int_{S_X}f_X(x)dx = \int^{\infty}_{-\infty}f_X(x)dx = 1 \\ \ \\
P(a < x < b) = \int^b_af_X(x)dx, \ a<b.
$$
### Expected Value
Recall the definition of the expected value of a discrete random variable:
$$ \mathbb{E}[X]=\sum_{S_X}xp_X(x)$$
We can replace the sum with an integral and the PMF with the PDF to get:
$$\mathbb{E}[X]=\int_{S_X}xf_X(x)dx$$
for the expected value of continuous random variable $X$. The LOTUS formula also applies:
$$E[g(X)] = \int_{S_X}g(x)f_X(x)dx$$
Also for $X \sim \text{Unif}(a,b)$ we have:
$$\mathbb{E}[X] = \frac{a+b}{2} \\ \ \\ \text{Var}(X) = \frac{(b-a)^2}{12}$$

## Normal Distribution
---
A continuous random variable $X$ follows a *normal distribution* ($X \sim N(\mu, \sigma^2)$ if, generally, its measurements fluctuate symmetrically around its mean. The PFD for such $X$ is:
$$ f_X(x)=\frac{1}{\sigma \sqrt{2\pi}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$
Fortunately, if we manage to make the parameters of the distribution $(\mu=0, \sigma^2 = 1)$, then there is a much easier PFD to work with. We do this by defining a new random variable as the old variable subtracted by its mean and divided by its standard deviation: $Z = \frac{X-\mu}{\sigma}$. Subtracting by $\mu$ shifts the center to $0$ and all other values around it symmetrically. Dividing by $\sigma$ scales the distances from the center (now $0$) in terms of the standard deviation. So now being $1$ away from the center means being $\sigma$ away from the center. Here, we say that $Z \sim N(0,1)$ and that we standardized $X$. Furthermore we have PFD:
$$\phi(z) = \frac{1}{\sqrt{2\pi}}e^{-\frac{z^2}{2}}$$
and CDF:
$$ \Phi(z) = P(Z \le z) = \int_{-\infty}^z\phi(u)du$$
Consequently,
$$P(a<Z<B) = \Phi(b) - \Phi(a)$$
## Joint Density Functions
---
Define a joint density function of continuous random variables $X$ and $Y$ as $f_{X,Y}(x,y)$. Then instead of thinking of the object that we are integrating over as a curve, it is now a surface. So integrating over an region gives us a volume that represents some positive probability. Then, a rectangle going from the 2D support to the function height has dimensions $h: f_{X,Y}(x,y), w: \Delta x, l: \Delta y$. So an approximation of the total volume under the surface using many of these small rectangles is:
$$ \sum f_{X,Y}(x,y) \Delta x \Delta y = 1$$
Taking the limit as these rectangles get infinitesimally small gives us:
$$\lim_{\Delta x, \Delta y \to 0}  \sum f_{X,Y}(x,y) \Delta x \Delta y  = \int_{S_{X,Y}} f_{X,Y}(x,y)dA$$
And the volume must sum to $1$:
$$\int_{S_{X,Y}} f_{X,Y}(x,y)dA = 1$$
Then, to integrate over a region that satisfies some restriction on $X$ or $Y$ (i.e. $(X,Y) \in A$), we simply integrate over the intersecting region between $A$ and $S_{X,Y}$:
$$P((X,Y) \in A) = \int_{S \cap A} f_{X,Y}(x,y)dA$$
### Marginals
Similar to how we recovered the marginals for a discrete joint probability distribution, we fix one variable and sum over all of the possible values of the other variable:
$$f_X(x) = \int_{-\infty}^{\infty}f_{X,Y}(x,y)dy \\ \ \\ f_Y(y) = \int^{\infty}_{-\infty} f_{X,Y}(x,y)dx$$
Note that the limits of integration can be replaced with the support of the integrating variable for that fixed interval. That is, if we have $S_{X,Y} = [0,1] \times [0,1]$ and we fix $x=0$ to get $f_X(0)$, then we draw a line along every possible $y$ value along $x=0$. In this case, the limits would be $0$ to $1$.

When we do this, we scan over the 3D joint density and keep a catalog of all $y$ values for which a function $f_Y(y)$ holds. i.e. we're finding the weight of the slice at $y$. If the limits of $x$ change, the rule for $f_y(y)$ will change, so we need to compute a different integral with adjusted limits. 
___