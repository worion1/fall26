<u> discrete random variables </u>
- expected value
	- formula ✓
- variance
	- formula ✓
	- alternative (practical) formula ✓
	- formula for standard deviation ✓
	- formula for variance of linear combination of $X$ ✓
	- formula for SD of linear combination of $X$ ✓
- joint probability distributions
	- recover joint with $p_{A,B}(a,b) = p_{A|B}(a|b)p_B(b)$
	- recover marginals
- conditional probability distributions
	- recover conditional with $p_{A|B}(a|b) = \frac{p_{A,B}(a,b)}{p_B(b)}$
	- find $p_{R|S}(r|S \in A)$
		- if $S_{R,S}$ is rectangular, then sum over $p_{R,S}(r,S \in A)$ in numerator and divide by $p_S(S \in A)$.
			- if $S_{R,S}$ is nonrectangular (choice of $r$ limits valid values of $s$), define piecewise by summing over valid values of $s$ for each $r$ in the numerator and divide by $p_S(S \in A)$.
	- recover marginals w/ multiplication rule
	- independence


<u> continuous random variables </u>
- PDFs
	-  Valid PDF
	- Interpretation of area under PDF as probability
	- Normalizing PDF
- CDFs
	- $F_X(t) = P(X \le t) = \int^t_{-\infty}f_X(u)du$
	- $P(a < X < b) = \int^b_a f_X(x)dx = F_X(b) - F_X(a)$
		- Doesn't have to be in the form $a < X \le b$ anymore!
		- $X \sim \text{Unif}(a,b) \implies F_X(x) = \frac{x-a}{b-a}$ in the support; *consider other regions*
- expected value
	- formula ✓
	- for cts random variables, expected value must always lie in the support
	- LOTUS for $g(X)$ ✓
	- $X \sim \text{Unif}(a,b) \implies \mathbb{E}[X] = \frac{a+b}{2}$ ✓
- variance
	- variance of linear combination formula ✓
	- $X \sim \text{Unif}(a,b) \implies \text{Var}(X) = \frac{(b-a)^2}{12}$ ✓
- exponential distribution $T \sim \text{Exp}(\lambda)$
	- PDF formula (and domain) ✓
	- CDF formula ✓
	- expected value formula ✓
	- second moment formula ✓
	- variance formula ✓
	- SD formula ✓
	- memorylessness
- normal distribution $X \sim \mathcal{N}(\mu, \sigma^2)$
	- non-standard PDF (note that domain is all reals) ✓
	- standard PDF (for $X \sim \mathcal{N}(\mu, \sigma^2)$) ✓
	- standard CDF ✓
	- standardization formula ✓
- continuous joint PDFs
	- $P((X,Y) \in A)$
		- formula
	- recover marginals
		- formulae
		- deploy horizontal/vertical line segments, if the limits change, split the integral and define the marginal as a piecewise.
	- $X,Y$ independence
- continuous conditional PDFs
	- formulae for $f_{X|Y}(x|y)$ and $f_{Y|X}(y|x)$
	- recover marginals with multiplication rule
	- why *do we* divide by $f_X(x)$ (or $f_Y(y)$) 
	- why *can we* divide by $f_X(x)$ (or $f_Y(y)$) even though $P(X=x)=P(Y=y)=0$ for cts r.v's.
	- independence
		- if $f_{Y|X}(y|x)$ has a variable support (such as $1 < y < x$), then its support varies with $x$. When the support changes, it gives us more information about the possible values of $Y$, which makes $X,Y$ dependent.
- conditional expected value
	- formulae for $\mathbb{E}[X|Y=y]$ and $\mathbb{E}[Y|X=x]$
		- conditioning on $X$ yields a function of $x$ and conditioning on $Y$ yields a function of $y$.
	- for discrete $A,B$ formulae for $\mathbb{E}[A|B=b]$ and reverse
- covariance
	- formula and range
	- alternative (practical) formula
	- $\text{Cov}(X + a, Y + b) = \text{Cov}(X,Y)$ because adding reals $a$ and $b$ just shift the mean and don't affect the spread of either random variable
	- LOTUS for expected value of $g(X,Y)$
	- interpretations of covariance being positive, zero, and negative
	- $X \perp Y \implies \text{Cov}(X,Y) = 0$
- correlation
	- formula and range
	- unitless
	- interpretations of correlation being positive, zero, and negative
	- $X \perp Y \implies \rho_{X,Y} = 0$
- For $X_1, \ldots, X_n$ with each $X_i$ i.i.d, mean $\mu$, variance $\sigma^2$
	- $S_n$
		- definition ✓
		- mean ✓
		- variance ✓
		- SD ✓
	- $\bar{X}_n$
		- definition ✓
		- mean✓ 
		- variance ✓
		- SD ✓
		- changing $n$ has no effect on $\sigma^2$ of each $X_i$ ✓
		- if $X_i = X_1$, then $\text{Var}(\bar{X}_n)$ is just $\sigma^2$. ✓
- For $K_n$ as a sum of $n$ i.i.d Bernoulli observations,
	- $K_n \sim \text{Bin}(n,p)$ ✓
	- mean ✓
	- variance ✓
	- $\frac{K_n}{n}$ is the proportion
		- mean ✓
		- variance ✓
- finding pdf of transformation of a random variable
	- For transformation $g(X)$ such that $Y = g(X)$ given $S_X = (a,b)$. 
		0) If not given, compute $F_X(x)$ by known distribution or integrating given $f_X(x)$.
		1) From $S_X$, deduce $S_Y$. 
			- 1a) *Easiest case*: If $g(x)$ is monotonic ($g'(x) >0$ or $g'(x) < 0$) and continuous over $S_X$,  then $S_Y = (\lim_{x\to a}g(x), \lim_{x\to b}g(x))$. Otherwise,

			- 1b) If $g(x)$ is not monotonic over $S_X$, then find these three values: $g(a)$ *lower boundary, $g(b)$ *upper boundary*, and $g(x_c)$ *local extrema* 
				(find by solving $g'(x) = 0$). For these values, if no other values lie between the minimum and maximum of them, then there are no interior thresholds. Else, every value in between the minimum and maximum are interior thresholds. 

				Alternatively, you can sketch the function $g(x)$ over $S_X$ and note the point(s) where the probability accumulation stops being symmetric (if it does). These point(s) (y value(s)) are the interior threshold(s).
				
				Note this interior threshold and move to step 2). Otherwise,

			- 1c) If $g(x)$ has a singularity within the support of $S_X$, consider what happens to $g(x)$ as it approaches that singularity. It will diverge, so break up the support into a union of the left of the singularity and the right of the singularity (if the right exists). e.g. If $g(x) = \frac{1}{x}$ and $S_X = (-1,2)$, then $S_Y = (-\infty, -1)\cup(\frac{1}{2},\infty)$. Otherwise,

			- 1d) If $S_X$ is disjoint (e.g. $S_X = (-1, 0) \cup (2, 3)$), each part of $S_X$ maps to parts of $S_Y$. Consider that $Y = X^2$. Then $(-1,0) \in S_X$ maps to $(0,1) \in S_Y$ and $(2,3) \in S_X$ maps to $(4,9) \in S_Y)$. Thus $S_Y = (0,1) \cup (4,9)$.

		2) Solve the event $\set{Y=g(X) \le y}$ for $X$.
			2a) For fully connected $S_Y$ (case 1a).
			 - i) Write $\set{g(X) \le y}$.
			 - ii) Manipulate this inequality to solve for $X$, keeping in mind that multiplying or dividing an inequality by a negative number flips the direction. If you want to multiply both sides by an expression containing $X$, consider $S_X$ to consider if the expression must be positive or negative. e.g. from HW5 problem 8c, multiplying by (1-X) multiplies by a positive number for $0<X<1$. From Midterm Prep problem 4a, $|1-U|$ simplifies to $1-U$ as $1-U > 0$ for 
			   $S_U = (0,1)$.
			   - iii) Result should be in the form $\set{X \le f(y)}$, $\set{X \ge f(y)}$, or
			   $\set{|X| \le f(y)} = \set{-f(y) \le X \le f(y)}$.
			2b) For case 1b)

		3) Write $F_Y(y)$ in terms of $F_X(x)$.
			3a) For fully connected $S_Y$.
			- i) Write $F_Y(y) = P(Y \le y)$ and substitute for whatever you found in step 2.
			- ii) Use these rules to rewrite as an expression in $F_X(x)$: $P(X \le f(y)) = F_X(f(y))$  $P(X \ge f(y)) = 1 - F_X(f(y))$, and $P(g(y) < X < f(y)) = F_X(f(y)) - F_X(g(y))$ for $g(y) < f(y)$. Note that the strictness of the inequalities are not significant here.
			- iii) Invoke the rule for $F_X(\text{something})$ that you found in step 0 to have an expression in $y$. Notably for $X \sim \text{Unif}(0,1)$, you just rewrite the argument of the $F_X(x)$.
			3b) For case 2b)
			
		4) Complete $F_Y(y)$ as piecewise, considering $S_Y$:
			4a) For fully connected $S_Y$
			- i) This should just be one piecewise $F_Y(y)$. Let $S_Y = (a,b)$ WLOG, then: $$F_Y(y) = \begin{cases} 0, & y \le a, \\ F_Y(y), & a < y < b, \\ 1, & y \ge b.\end{cases}$$
			4b) For case 3b)
			
		5) Find $f_Y(y) = F_Y'(y)$.
			5a) For fully connected $S_Y$ / singular $F_Y(y)$:
			- i) Differentiate the singular $F_Y(y)$ that you found. Rewrite $f_Y(y)$ to be piecewise to consider that $f_Y(y) = 0$ outside of $S_Y$. $$ f_Y(y) = \begin{cases}F'_Y(y), & y \in S_Y, \\ 0, & \text{otherwise.} \end{cases}$$
			5b) For case 4b)
		
			
			