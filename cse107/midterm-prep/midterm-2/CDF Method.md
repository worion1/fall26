- For transformation $g(X)$ such that $Y = g(X)$ given $S_X = (a,b)$. 
	0) If not given, compute $F_X(x)$ by known distribution or integrating given $f_X(x)$.
	1) From $S_X$, deduce $S_Y$. 
		- 1a) *Easiest case*: If $g(x)$ is monotonic (equivalently, injective; $g'(x) >0$ or $g'(x) < 0$) and continuous over $S_X$, then if it is monotonically increasing: $S_Y = (\lim_{x\to a}g(x), \lim_{x\to b}g(x))$. If it is monotonically decreasing: $S_Y = (\lim_{x\to b}g(x), \lim_{x\to a}g(x))$ Otherwise,

		- 1b) If $g(x)$ is not monotonic over $S_X$, then find these three values: $g(a)$ *lower boundary*, $g(b)$ *upper boundary*, and $g(x_c)$ *local extrema* 
			(find by solving $g'(x) = 0$). Order these least to greatest as a set. If $g(a) \ne g(b)$, then $g(x_c)$ is your interior threshold. If $g(a) = g(b)$, then there is no interior threshold.

			Alternatively, you can sketch the function $g(x)$ over $S_X$ and note the intervals where $g(x)$ is locally injective and not locally injective. The $y$ value(s) at which this shift occurs is the interior threshold. For $g(x)=x^2$ on $(-1,2)$, $g(x)$ is not locally injective on $(-1,1)$, but becomes locally injective on $(1,2)$. So $y=1$ is the interior threshold, so we split $S_Y$ into $(0,1)$ and $(1,4)$ for this specific case.
			
			**$S_Y$ is still the minimum to the maximum values of $g(x)$ over $S_X$**, however we will need to partition this support by the found interior threshold in step 2. 

	2) Solve the event $\set{Y=g(X) \le y}$ for $X$.
		2a) For fully connected $S_Y$ (case 1a).
		 - i) Write $\set{g(X) \le y}$.
		 - ii) Manipulate this inequality to solve for $X$, keeping in mind that multiplying or dividing an inequality by a negative number flips the direction. If you want to multiply both sides by an expression containing $X$, consider $S_X$ to consider if the expression must be positive or negative. e.g. from HW5 problem 8c, multiplying by (1-X) multiplies by a positive number for $0<X<1$. From Midterm Prep problem 4a, $|1-U|$ simplifies to $1-U$ as $1-U > 0$ for 
		   $S_U = (0,1)$.
		   - iii) Result should be in the form $\set{X \le f(y)}$, $\set{X \ge f(y)}$, or
		   $\set{|X| \le f(y)} = \set{-f(y) \le X \le f(y)}$.
		2b) For case 1b).
		- i) Partition $S_Y$ by the interior threshold (lets call it $y^*$). Then write "For $a < y < y^*$" and "$y^* < y < b$" and apply the following steps for each interval
		- ii) Rewrite the event $\set{g(X) \le y}$ by isolating $X$ *considering the above intervals* and whether the resulting event lies within $S_X$. Since we will write something like $X \le f(y)$, we must make sure that $X$ can *actually be that value* for the specified support of $Y$ (either $(a, y^*)$ or $(y^*, b)$). To determine if the resulting interval that we find from this process is contained entirely by $S_X$, take the intersection. The result will be the interval/event used in part 3) for that specific partitioning interval of $S_Y$. 

	3) Write $F_Y(y)$ in terms of $F_X(x)$.
		3a) For fully connected $S_Y$.
		- i) Write $F_Y(y) = P(Y \le y)$ and substitute for whatever you found in step 2.
		- ii) Use these rules to rewrite as an expression in $F_X(x)$: $P(X \le f(y)) = F_X(f(y))$  $P(X \ge f(y)) = 1 - F_X(f(y))$, and $P(g(y) < X < f(y)) = F_X(f(y)) - F_X(g(y))$ for $g(y) < f(y)$. Note that the strictness of the inequalities are not significant here.
		- iii) Invoke the rule for $F_X(\text{something})$ that you found in step 0 to have an expression in $y$. Notably for $X \sim \text{Unif}(0,1)$, you just rewrite the argument of the $F_X(x)$.
		3b) For case 2b).
		- i) Write $F_Y(y) = P(Y \le y)$ *for each partitioning interval of $S_Y$* and substitute your results from step 2.
		- ii) Use the above steps (3a) to get $F_Y(y)$ as a function of $y$ (fully independent of F_X(x) terms). In the end you should have $F_{Y1}(y)$ and $F_{Y2}(y)$ for the two partitioning intervals.
		
	4) Complete $F_Y(y)$ as piecewise, considering $S_Y$:
		4a) For fully connected $S_Y$
		- i) This should just be one piecewise $F_Y(y)$. WLOG let $S_Y = (a,b)$, then: $$F_Y(y) = \begin{cases} 0, & y \le a, \\ F_Y(y), & a < y < b, \\ 1, & y \ge b.\end{cases}$$
		4b) For case 3b)
		- i) This should be one piecewise $F_Y(y)$ with two separate rules for each partitioning intervals of $S_Y$:
		  $$F_Y(y) = \begin{cases} 0, & y \le a, \\ F_{Y1}(y), & a < y < y^*, \\ F_{Y2}(y), & y^* \le y < b,\\ 1, & y \ge b.\end{cases} $$
		
	5) Find $f_Y(y) = F_Y'(y)$.
		5a) For fully connected $S_Y$ / singular $F_Y(y)$:
		- i) Differentiate the rule for $F_Y(y)$ that you found. Rewrite $f_Y(y)$ to be piecewise to consider that $f_Y(y) = 0$ outside of $S_Y$. $$ f_Y(y) = \begin{cases}F'_Y(y), & y \in S_Y, \\ 0, & \text{otherwise.} \end{cases}$$
		5b) For case 4b)
		- i) Differentiate the two rules that you found $F_Y(y)$ and set them to be valid on their respective partitioning intervals: $$ f_Y(y) = \begin{cases}F'_{Y1}(y), & a < y < y^*,\\F'_{Y2}(y), & y^*\le y<b \\ 0, & \text{otherwise.} \end{cases}$$