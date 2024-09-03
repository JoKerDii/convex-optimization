# Convex Functions

Contents:

* Basic properties and examples
* Operations that preserve convexity
* The conjugate function
* Quasiconvex functions
* Log-concave and log-convex functions
* Convexity with respect to generalized inequalities

## Basic Properties and Examples

A function $f: \mathbf{R}^n \rightarrow \mathbf{R}$ is convex if its domain $\text{dom} f$ is a convex set and if it satisfies the following condition $f(\theta x+(1-\theta)y) \leq \theta f(x) + (1-\theta)f(y)$, for all $x,y \in \text{dom} f, 0 \leq \theta \leq 1$.

* $f$ is concave if $-f$ is convex
* $f$ is strictly convex if $\text{dom} f$ is convex and $f(\theta x) + (1-\theta)y < \theta f(x) + (1-\theta) f(y)$, for $x,y \in \text{dom} f, x \neq y, 0 < \theta < 1$.

### Examples on $\mathbf{R}$:

Convex:

* Affine: $ax+b$ on $\mathbf{R}$, for any $a,b \in \mathbf{R}$
* Exponential: $e^{ax}$, for any $a \in \mathbf{R}$
* Powers: $x^\alpha$ on $\mathbf{R}_{++}$, for $\alpha \geq 1$ or $\alpha \leq 0$
* Powers of absolute value: $|x|^p$ on $\mathbf{R}$, for $p\geq 1$
* Negative entropy: $x\log x$ on $\mathbf{R}_{++}$

Concave:

* Affine: $ax+b$ on $\mathbf{R}$, for any $a,b \in \mathbf{R}$
* Powers: $x^{\alpha}$ on $\mathbf{R}_{++}$, for $0 \leq \alpha \leq 1$
* Logarithm: $\log x$ on $\mathbf{R}_{++}$

### Examples on $\mathbf{R}^n$ and $\mathbf{R}^{m \times n}$

Affine functions are convex and concave; all norms are convex

Examples on $\mathbf{R}^n$:

* Affine function $f(x) = a^Tx + b$
* Norms: $\|x\|_p = (\sum_{i=1}^n |x_i|^{1/p})$ for $p \geq 1$; $\|x\|_{\infin} = \max_k|x_k|$

Example on $\mathbf{R}^{m\times n}$ ($m \times n$ matrix)

* Affine function

  $f(x) = tr(A^X) + b = \sum^m_{i=1} \sum^n_{i=1} A_{ij}X_{ij}+b$

* Spectral (maximum singular value) norm

  $f(x) = \|x\|_2 = \sigma_{max}(X) = (\lambda_{max}(X^T X))^{1/2}$

### Restriction of a convex function to a line

$f: \mathbf{R}^n  \rightarrow \mathbf{R}$ in convex if and only if the function $g : \mathbf{R} \rightarrow \mathbf{R}, g(t) = f(x+tv)$, $\text{dom} g = \{t|x+tv \in \text{dom} f\}$ is convex (in $t$) for any $x \in \text{dom} f, v\in\mathbf{R}^n$.

Can check convexity of $f$ by checking convexity of functions of one variable.

Example: $f: \mathbf{S}^n \rightarrow \mathbf{R}$ with $f(X) = \log \det X, \text{dom} f = \mathbf{S}_{++}^n$
$$
\begin{aligned}
g(t) = \log \det (X + tV) 
&= \log \det (X^{1/2}(I + tX^{-1/2}VX^{-1/2})X^{1/2})\\
&= \log \det X +\log \det(I + t\lambda^{-1/2}VX^{-1/2})\\
&=\log \det X + \sum^n_{i=1} \log(1+t\lambda_i)\\
\end{aligned}
$$
where $\lambda_i$ are the eigenvalues of $X^{-1/2}VX^{-1/2}$, $g$ is concave in $t$ (for any choice of $X \succ 0, V$); hence $f$ is concave.

### Extended-value extension

Extended-value extension $\tilde{f}$ of $f$ is $\tilde{f}(x)=f(x),x \in \text{dom} f; \tilde{f}(x) = \infin, x \not\in \text{dom} f$.

Often simplified notation; e.g., the condition $0\leq \theta \leq 1 \implies \tilde{f}(\theta x + (1-\theta)y) \leq \theta \tilde{f}(x) + (1-\theta) \tilde{f}(y)$. (As an inequality in $\mathbf{R}\cup \{\infin\}$), means the same as the two conditions

* $\text{dom} f$ is convex

* For $x,y \in \text{dom} f$,

  $0 \leq \theta \leq 1 \implies f(\theta x + (1-\theta)y) \leq \theta f(x) + (1-\theta)f(y)$.

### First-order condition

$f$ is **differentiable** if $\text{dom} f$ is open and the gradient $\nabla f(x) = \big({\partial f(x)\over\partial x_1}, {\partial f(x)\over\partial x_2}, ..., {\partial f(x)\over\partial x_n}\big) $ exists at each $x \in \text{dom }f$.

**1st-order condition**: differentiable $f$ with convex domain is convex iff $f(y)\geq f(x)+\nabla f(x)^T (y-x),$ for all $x,y \in \text{dom} f$.

Note that $f(x)+\nabla f(x)^T (y-x)$ is an affine function of $y$, and it's the first order Taylor expansion of $f$ at $x$. This function is really close to $f$ if you are close to $x$. 

$f(y)\geq f(x)+\nabla f(x)^T (y-x)$ means the function is bigger everywhere globally than the first order Taylor series expansion. 

### Second-orde condition

$f$ is **twice differentiable** if $\text{dom} f$ is open and the Hessian $\nabla^2 f(x) \in \mathbf{S}^n$, $\nabla^2f(x)_{ij}=  { \partial^2f(x)\over \partial x_i\partial x_j }$, $i,j = 1, ..., n$, exists at each $x \in \text{dom} f$.

**2nd-order conditions**: for twice differentiable $f$ with convex domain

* $f$ is convex if and only if $\nabla^2f(x) \succeq 0$ (Hessian is positive semi definite), for all $x \in \text{dom} f$.

* If $\nabla^2f(x)\succ0$ (Hessian is positive definite) for all $x \in \text{dom} f$, then $f$ is strictly convex.

  It's false the other way around. You actually can be strictly convex without having the Hessian positive definite for all points in the domain.

### Example

**Quadratic function**: $f(x)=(1/2)x^TPx+q^Tx+r$ (With $P \in \mathbf{S}^n$)

$\nabla f(x) = Px+q, \space \nabla^2 f(x)=P$

Convex if $P \succeq0$.

**Least-squares objective**: $f(x)=\|Ax-b\|_2^2$

$\nabla f(x) = 2A^T(Ab-b), \space \nabla^2f(x)=2A^TA$

Convex for any $A$, because Hessian is always positive semi definite.

**Quadratic-over-linear**: $f(x,y)=x^2/y$

$\nabla^2 f(x,y) = {2 \over y^3} \begin{bmatrix}y\\-x \end{bmatrix} \begin{bmatrix}y\\-x \end{bmatrix}^T \succeq 0$

Convex for $y>0$ because the Hessian is rank 1 and positive semi definite.

**Log-sum-exp**: $f(x)=\log \sum_{k=1}^n \exp x_k$ is convex

$\nabla^2 f(x) = {1\over \mathbf{1}^Tz} \mathbf{diag}(z) - {1\over (\mathbf{1}^Tz)^2} zz^T, (z_k =  \exp x_k)$ , 

to show $\nabla^2f(x) \succeq 0$, we must verify that $v^T \nabla^2f(x)v \geq 0$ for all $v$:

$v^T\nabla^2f(x)v = {(\sum_kz_kv_k^2)(\sum_kz_k)-(\sum_kv_kz_k)^2\over (\sum_kz_k)^2}\geq 0$

Since $(\sum_kz_kv_k^2)(\sum_kz_k)\geq (\sum_kv_kz_k)^2$ (From Cauchy-Schwarz inequality)

**Geometric mean**: $f(x) = (\prod_{k=1}^n x_k)^{1/n}$ on $\mathbf{R}_{++}^n$ is concave (similar proof as for log-sum-exp).

### Epigraph and sublevel set

**$\alpha-$sublevel set** of $f: \mathbf{R}^n \rightarrow \mathbf{R}$:

$C_{\alpha} = \{x \in \text{dom} f| f(x) \leq \alpha \}$

Sublevel sets of convex functions are convex (converse is false)

**Epigraph** of $f: \mathbf{R}^n \rightarrow \mathbf{R}$:

$\text{epi} f = \{(x,t) \in \mathbf{R}^{n+1}| x \in \text{dom}f, f(x) \leq t\}$

$f$ is convex if and only if $\text{epi} f $ is a convex set. So the real connection between convex functions and convex sets is through the epigraph.

### Jensen's inequality

**Basic inequality**: if $f$ is convex, then for $0 \leq \theta \leq 1$, 

$f(\theta x + (1-\theta)y) \leq \theta f(x) + (1-\theta)f(y)$

**Extension**: if $f$ is convex, then $f(\mathbf{E}z) \leq \mathbf{E}f(z)$ for any random variable $z$.

Basic inequality is a special case with discrete distribution $P(z=x)=\theta, P(z=y)=1-\theta$.

## Operations that Preserve Convexity

Practical methods for establishing convexity of a function

1. Verify definition (often simplified by restricting to a line)
2. For twice differentiable functions, show $\nabla^2 f(x) \succeq 0$
3. Show that $f$ is obtained from simple convex functions by operations that preserve convexity
   * Nonnegative weighted sum
   * Composition with affine function
   * Pointwise maximum and supremum
   * Composition 
   * Minimization 
   * Perspective

### Positive Weighted Sum & Composition with Affine Function

**Nonnegative multiple**: $\alpha f$ is convex if $f$ is convex, $\alpha \geq 0$.

**Sum**: $f_1 + f_2$ convex if $f_1, f_2$ convex (extends to infinite sums, integrals)

**Composition with affine function**: $f(Ax+b)$ is convex if $f$ is convex.

**Example:** 

* Log barrier for linear inequalities

  $f(x) = -\sum^m_{i=1}\log(b_i-a_i^Tx),  \space \text{dom} f = \{x | a_i^Tx < b_i, i = 1, ..., m\}$

  This is a convex function called 'logarithmic barrier function' for the domain which is an open polyheron.

  It's called logarithmic barrier function because when it goes closer to the boundary, $b_i-a_i^Tx$ will be very small and the $f(x)$ will go infinitely positive large.

* (any) norm of affine function: $f(x) = \|Ax+b\|$

### Pointwise Maximum

If $f_1, ..., f_m$ are convex, then $f(x)=\max\{f_1(x), ...., f_m(x)\}$ is convex. 

(Note that this does not guarantee differentiability. Actually, differentiability does not play a critical role in convexity. This is a first hint that convex optimization does not require much calculus.)

Example:

* Piecewise-linear function: $f(x)=\max_{i=1,...,m}(a_i^Tx+b_i)$ is convex

* Sum of $r$ largest components of $x \in \mathbf{R}^n$:

  $f(x)=x_{[1]}+x_{[2]}+...+x_{[r]}$ is convex ($x_{[i]}$ is $i$th largest component of $x$)

  Proof: $f(x) = \max \{x_{i_1} + x_{i_2} + ... + x_{i_r}| 1 \leq i_i < i_2 < ... < i_r \leq n\}$

### Pointwise Supremum

If $f(x,y)$ is convex in $x$ for each $y\in A$, then $g(x) = \sup_{y\in A} f(x,y)$ is convex.

Example: 

* Support function of a set $C$: $S_C(x) = \sup_{y\in C} y^Tx$ is convex

* Distance to farthest point ini a set $C$:

  $f(x)=\sup_{y\in C} \|x-y\|$

* Maximum eigenvalue of symmetric matrix: for $X\ in S^n$:

  $\lambda_{max}(X) = \sup_{\|y\|_2=1} y^TX y $ 

### Composition with Scalar functions

Composition of $g$: $\mathbf{R}^n \rightarrow \mathbf{R}$ and $h: \mathbf{R} \rightarrow \mathbf{R}:$ $f(x) = h(g(x))$

$f$ is convex if

1. $g$ convex, $h$ convex, $\tilde{h}$ non decreasing. ($\tilde{h}$ is extended-value extension of $h$)
2. $g$ concave, $h$ convex, $\tilde{h}$ non increasing. ($\tilde{h}$ is extended-value extension of $h$)

* Proof (for $n=1$, differentiable $g,h$)

  $f''(x) = h''(g(x))g'(x)^2 + h'(g(x))g''(x)$

* Note: monotonicity must hold for extended-value extension $\tilde{h}$, because of $h'(g(x))$ part in the second derivative function.

Examples:

* $\exp g(x)$ is convex if $g$ if convex
* $1/g(x)$ is convex if $g$ is concave and positive

### Vector Composition

Composition of $g:\mathbf{R}^n \rightarrow \mathbf{R}^k$ and $h: \mathbf{R}^k \rightarrow \mathbf{R}$:

$f(x)=h(g(x)) = h(g_1(x),g_2(x), ..., g_k(x))$

$f$ is convex if 

1. $g_i$ convex, $h$ convex,  $\tilde{h}$ is non decreasing in each argument
2. $g_i$ concave, $h$ convex,  $\tilde{h}$ is non increasing in each argument

Proof (for $n=1$, differentiable $g,h$)

$f''(x)= g'(x)^T\nabla^2h(g(x))g'(x) + \nabla h(g(x))^Tg''(x)$

Defined in another way: $f$ is convex if for each $i$,

1. $g_i$ is affine
2. $g_i$ is convex and $h$ is increasing in each argument $i$
3. $g_i$ is concave and $h$ is decreasing in each argument $i$

Examples:

* $\sum_{i=1}^m \log g_i(x)$ is concave if $g_i$ are concave and positive

* $\log \sum_{i=1}^m \exp g_i(x)$ is convex if $g_i$ are convex.

  Log sum $x$ function is convex. it's increasing in each argument.

### Minimization

If $f(x,y)$ is convex in $(x,y)$ and $C$ is a convex set, then $g(x)=\inf_{y\in C} f(x,y)$ is convex. (Partial minimization of $f$ preserves convexity).

Examples:

* $f(x,y) = x^TAx + 2x^TBy + y^TCy$ with $\begin{bmatrix} A & B \\ B^T & C \end{bmatrix} \succeq 0, C \succ0$, 

  minimizing over $y$ gives $g(x) = \inf_y f(x,y)= x^T(A-BC^{-1}B^T)x$

  $g$ is convex, hence **Schur complement** $A-BC^{-1}B^T \succeq0$

  Note that quadratic functions actually are preserved under partial minimization.

* Distance to a set: $\text{dist}(x,S) = \inf_{y\in S} \|x-y\|$ is convex if $S$ is convex.

### Perspective

The **perspective** of a function $f:\mathbf{R}^n \rightarrow \mathbf{R}$ is the function $g: \mathbf{R}^n \times \mathbf{R} \rightarrow \mathbf{R}$, 

(perspective is a function on the graph space, it takes two arguments $x, t$)

$g(x,t)=tf(x/t), \space \text{dom} g = \{(x,t)| x/t \in \text{dom} f,t > 0\}$

$g$ is convex if $f$ is convex.

Example: 

* $f(x) = x^Tx$ is convex; hence $g(x,t)=t(x/t)^T(x/t)=x^Tx / t$ is convex for $t>0$
* Negative logarithm $f(x)=-\log x$ is convex; hence relative entropy $g(x,t)=t\log t - t\log x$ is convex on $\mathbf{R}_{++}^2$.
* If $f$ is convex, then $g(x)=(c^Tx+d)f((Ax+b)/(c^Tx+d))$ is convex on $\{x | c^Tx +d > 0, (Ax+b)/(c^xx+d) \in \text{dom} f\}$

## The Conjugate Function

The **conjugate** of a function $f$ is $f^*(x)=\sup_{x \in \text{dom}f} (y^Tx-f(x))$

You have function $f(x)$ and linear function $y^T x$ or $xy$, you move $xy$ until it touches a point of $f(x)$ so that $y^T x - f(x)$ is minimized. The the height of $yx$ would be negative conjugate $f^*(x)$. If $y$ increases, conjugate goes up. (Thinking about changing from x to 2x). 

* $f^*$ is convex (even if $f$ is not).

Examples:

* Negative logarithm $f(x)=-\log x$

  $f^*(y) = \sup_{x>0} (xy+\log x) = \begin{cases}-1-\log(-y), & y< 0\\ \infin, & \text{otherwise} \end{cases}$

* Strictly convex quadratic $f(x)=(1/2)x^TQx$ with $Q\in S_{++}^n$

  $f^*(y) = \sup_x(y^x-(1/2)x^TQx) = 1/2 y^TQ^{-1}y$

  The conjugate of a quadratic form is the quadratic form with the inverse matrix.

## Quasiconvex Functions

## Log-Concave and Log-Convex Functions

## Convexity w.r.t. Generalized Inequalities

