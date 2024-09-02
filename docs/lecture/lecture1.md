# Convex Sets

Content:

* Affine and convex sets
* Some important examples
* Operations that preserve convexity
* Generalized inequalities
* Separating and supporting hyperplanes
* Dual cones and generalized inequalities

## Affine Set and Convex Set

**Affine set**: A line through points $x_1, x_2$ is all points that $x=\theta x_1 + (1-\theta) x_2, (\theta \in \text{R})$. An affine set is a set where if you have two distinct points in the set then the line that passes through it is contained entirely in the set.

Example: solution set of linear equations $\{x| Ax=b\}$ is an affine set. Conversely, every affine set can be expressed as solution set of system of linear equations.

Verification of "affine set is a solution set of system of linear equations": 

Let's define a line as $x = \theta x_1+ (1-\theta) x_2, \space (\theta \in \bold{R})$, and a linear equation as $Ax=b$, then
$$
\begin{aligned}
Ax_1 &= b, \space Ax_2 = b\\
Ax &= A(\theta x_1 + (1-\theta) x_2)\\
&=\theta A x_1 + (1-\theta) A x_2\\
&= \theta b + (1-\theta) b\\
&= b
\end{aligned}
$$
**Convex set**: A line segment is all points that $x=\theta x_1 + (1-\theta) x_2$ between $x_1$ and $x_2$, with $0 \leq \theta \leq 1$. Convex set contains line segment between any two points in the set. In other words, if you have $x_1, x_2$ in the set, there must be a clear line of sight path between $x_1, x_2$ within the set. $x_1, x_2 \in \text{C}, 0\leq \theta \leq 1 \implies \theta x_1 + (1-\theta) x_2 \in \text{C}$.

**Convex hull** $conv \space S$: Convex combination in $x_1, .., x_k$ is any point $x$ of the form $x = \theta_1 x_1 + \theta_2 x_2 + ... + \theta_k x_k$, where $\theta_1 + ... + \theta_2, \theta_i \geq 0$. Convex hull is a set contains all convex combinations of points in a set $S$. 

**Convex cone**: Conic (nonnegative) combination of $x_1, x_2$ is any point $x$ of the form $x = \theta_1 x_1 + \theta_2 x_2$, with $\theta_1\geq 0, \theta_2 \geq 0$. Geometrically, conic combination is a pie slice that goes between $x_1, x_2$, and 0. It sits in a plane, even if $x_1, x_2$ are in a high dimensional space, the set of conic combinations lies in a plane that passes through 0, $x_1$, and $x_2$. Convex cone is a set that contains all conic combinations of points in the set.

**Hyperplane**: A hyperplane is a solution set of a single linear equation. A set of form $\{x|a^T x = b\} \space (a\neq 0)$. 

* In $\text{R}^2$ it's a line. In $\text{R}^3$, it's a plane. In higher dimensions, it's a hyperplane.
* $a$ is a normal vector to that hyperplane.
* Hyperplanes are affine and convex

**Halfspace**: a set of the form $\{x | a^T x \leq b\} \space (a \neq 0)$. 

* Halfspaces are convex but not affine
* $a$ is a normal vector.

If we take two points in a halfspace, the question is whether the segment is in it? The answer is obvious yes. The verification is as follows:
$$
\begin{aligned}
a^Tx_1 &\leq b, \space a^T x_2 \leq b\\
x &=\theta x_1 + (1-\theta) x_2, \theta \in [0,1] \\
a^T x &= a^T (\theta x_1 + (1-\theta) x_2)\\
&=\theta a^T x_1 + (1-\theta) a^T x_2\\
&\leq \theta b + (1-\theta) b
\end{aligned}
$$
**(Euclidean) ball** with center $x_c$ and radius $r$ can be expressed as $B(x_c,r) = \{x \space | \space \|x-x_c\|_2 \leq r \} = \{x_c + ru \space|\space \|u\|_2 \leq 1 \}$.

**Ellipsoid**: a set of the form $\{ x\space|\space (x-x_c)^T P^{-1} (x-x_c) \leq 1\}$, with $P \in \text{S}^n_{++}$ (i.e. $P$ symmetric positive definite). Other representation: $\{x_c + Au \space|\space \|u\|_2 \leq 1 \}$ with $A$ square and nonsingular. If $P = r^2 I$, then the set is a euclidean ball and also an ellipsoid.

**Norm**: is a function $\| · \|$ that satisfiies

* Positive definiteness: $\|x \| \geq 0; \|x\|=0$ if and only if $x=0$
* Homogeneous of degree 1: $\|tx\|= |t| \|x \|$ for $t \in \text{R}$
* Triangle inequality: $\|x+y\| \leq \|x\| + \|y\|$

The notation $\|·\|$ is general (unspecified) norm; $\|·\|$ is particular norm. e.g. $\|x\|_2 = \sqrt{x_1^2 + .. x_n^2}$

**Norm ball** with center $x_c$ and radius r: $\{x \space|\space \|x-x_c\|\leq r\}$

**Norm cone**: $\{(x,t) \space | \space \|x\| \leq t\}$

* Euclidean norm cone is called second-order cone.
* Norm balls and cones are convex.

**Polyhedron** is a solution set of finitely many linear inequalities and equalities: $Ax \preccurlyeq b, \space Cx = d$. ($A \in \text{R}^{m\times n}, C \in \text{R}^{p \times n}, \preccurlyeq$ is componentwise inequality). Polyhedron is intersection of finite number of halfspaces and hyperplanes.

**Positive semidefinite cone**: 

* $\text{S}^n$ is set of symmetric $n\times n$ matrices.

* $\text{S}_+^n=\{X \in \text{S}^n \space | \space X \succcurlyeq 0 \}$: positive semidefinite $n \times n$ matrices.

  $X \in \text{S}_+^n \longleftrightarrow z^TXz \geq 0$ for all $z$.

  $\text{S}_+^2$ is a convex cone. This means if you take two positive semidefinite matrices and you take a non-negative linear combination, then you get another positive semidefinite matrices.

* $\text{S}_{++}^n = \{X \in \text{S}^n \space | X \succ 0\}$: positive definite $n \times n$ matrices. 

  Example:  $ \begin{bmatrix} 
      x&y\\
      y&z\\
   \end{bmatrix} \in \text{S}^2_+$.

## Operations that Preserve Convexity

Practical methods for establishing convexity of a set $C$:

1. Apply definition

   $x_1,x_2 \in C, \space 0 \leq \theta \leq 1 \space \implies \theta x_1 + (1-\theta)x_2 \in C$

2. Show that $C$ is obtained from simple convex sets (hyperplanes, halfspaces, norm balls, ...) by operations that preserve convexity

   * Intersection
   * Affine functions
   * Perspective function
   * Linear-fractional functions

### Intersection

The intersection of (any number of) convex sets is convex.

Example: $S = \{x \in \text{R}^m \space | \space |p(t)| \leq 1 \text{ for } |t| \leq \pi/3\}$, where $p(t) = x_1 \cos t+x_2 \cos 2t + ... + x_m \cos mt$. In other words, if $S_t = \{x \in \text{R}^m \space | \space |p(t)| \leq 1\}$, then $S = \cap_{0 \leq t\leq \pi/3} S_t$.

### Affine Functions

Affine functions preserve convexity in both directions, both forward and reverse.

Suppose $f : \text{R}^n \rightarrow \text{R}^m$ is affine ($f(x) = Ax+b$ with $A\in \text{R}^{m\times n}, b\in \text{R}^m$)

* The image of a convex set under $f$ is convex

  $S \subseteq\text{R}^n$ convex $\implies$ $f(S) = \{f(x) \space | \space x \in S\}$ convex

* The inverse image $f^{-1}(C)$ of a convex set under $f$ is convex

  $C\subseteq \text{R}^m$ convex $\implies$ $f^{-1}(C) = \{x \in \text{R}^n \space | \space f(x) \in C\}$ convex

  $f^{-1}(C)$ is defined for a set, even in cases when $f$ is not invertible and $f^{-1}(·)$ does not exist, $f$ inverse the relation does.

Examples:

* Scaling, translation, projection

* Solution set of linear matrix inequality $\{x \space | \space x_1 A_1 + ... + x_m A_m \preccurlyeq B\}$ (with $A_i, B \in \text{S}^p$).

  The way we know this linear matrix inequality is convex is because we can form the affine function $f(x) = B - \sum_{i=1}x_iA_i$.

* Hyperbolic cone $\{x \space | \space x^TPx \leq (c^Tx)^2, c^Tx \geq 0\}$ (with $P \in \text{S}_+^n$) is convex, because it's the standard or norm cone under an affine mapping.

### Perspective Function

$P: \text{R}^{n+1} \rightarrow \text{R}^n$: $P(x,t) = x/t, \space \text{dom} P = \{(x,t) \space | \space t > 0\}$.

Images and inverse images of convex sets under perspective are convex.

### Linear-Fractional Functions

$f : \text{R}^n \rightarrow \text{R}^m, f(x) = {Ax+b \over c^x + d}, \space \text{dom} f = \{x \space | \space c^T x + d = 0 \}$:

Image and inverse images of convex sets under linear-fractional functions are convex.

## Generalized inequalities

A convex cone $K \subseteq \text{R}^n$ is a **proper cone** if 

* $K$ is closed (contains it boundary)
* $K$ is solid (has nonempty interior)
* $K$ is pointed (contains no line)

Examples: 

* Nonnegative orthant $K = \text{R}_+^n= \{ x \in \text{R}^n \space | \space x_i \geq 0, i=1,...,n\}$ 
* Poistive semidefinite cone $K = S_+^n$
* Nonnegative polynomials on $[0,1]$: $K = \{x \in \text{R}^n \space | \space x_1 + x_2 t+ x_3 t^2 + ... + x_n t^{n-1} \geq 0 \text{ for } t \in [0,1]\}$

**Generalized inequality** defined by a proper cone $K$: $x \preccurlyeq_K y \longleftrightarrow y-x \in K$, $x \prec_k y \longleftrightarrow y-x \in \text{int} K $

Examples:

* Componentwise inequality ($K = \text{R}_+^n$)

  $x \preccurlyeq_{\text{R}_+^n} y \longleftrightarrow x_i \leq y_i, i=1,...,n$

* Matrix inequality ($K = \text{S}_+^n$)

  $X \preccurlyeq _{\text{S}_+^n} Y \longleftrightarrow Y-X$ positive semidefinite

  If you see $x \preccurlyeq y$ or $X \preccurlyeq Y$, the default is that it's with respect to $\text{S}_+^n$ convex cone (positive semidefinite cone).

**Minimum and minimal elements**:

$\preccurlyeq_K$ is not in general a linear ordering: we can have $x\not\preccurlyeq_K y$ and $y \not\preccurlyeq_K x$ (incomparable).

$x\in S$ is **the** **minimum element** of $S$ with respect to $\preccurlyeq_K$ if $y\in S \implies x \preccurlyeq_K y$

$x \in S$ is **a** **minimal element** of $S$ with respect to $\preccurlyeq_K$ if $y \in S, y \preccurlyeq_K x \implies y=x$

## Separating and Supporting Hyperplanes

If $C$ and $D$ are disjoint convex sets, then

There is a hyperplane $\{x | a^Tx = b\}$ separates the set $C$ and set $D$, or there is a linear classifier that distinguishes set $C$ and set $D$. Or say there exists $a\neq 0, b$ that the affine function $a^T x \leq b$ for $x \in C$ and $a^T x \geq b$ for $x \in D$. strict separation requires additional assumptions (e.g. $C$ is closed, $D$ is a singleton).

**Supporting hyperplane** to set $C$ at boundary point $x_0$: $\{x | a^Tx = a^Tx_0\}$, where $a \neq 0$ and $a^Tx \leq a^T x_0$ for all $x \in C$. In other words, there is a linear inequality or a halfspace which does not intersect $C$ but has a point on the boundary of $C$. 

> Quiz: A point $x_0$ on the boundary of a convex set uniquely defines a supporting hyperplane for the set at that point.
>
> Answer: False
>
> Explanation: If $x_0$ is, for example, the corner of a square in $\text{R}^2$, then there are infinitely many supporting hyperplanes at that point.

## Dual cones and generalized inequalities

**Dual cone** is the set of vectors that make a non-negative inner product with every element of this cone.

Dual cone of a cone $K$: $K^* = \{y \space |\space y^T x \geq 0 \text{ for all } x \in K\}$.

To see if a point $y$ is in $K^*$, we look at the space where every point can make a non-negative inner product with $y$, if all element of cone $K$ is in that space, then we can say that this point $y$ is definitely in $K^*$: $y \in K^*$.

If $K$ is thin and sharp, then $K^*$ is thick and blunt. 90 degree $K$ is self dual.

Example: 

* $K=\text{R}^n_+: K^*=\text{R}^n_+$: a vector is non negative, if and only if, it makes a non negative inner product with all non negative vectors.
* $K=\text{S}^n_+:K^*=\text{S}^n_+$: a matrix is positive semi definite if and only if its trace against all positive semi definite matrices is non negative.
* $K = \{(x,t) \space | \space \|x\|_2 \leq t\} : K* = \{(x,t) \space | \space \|x\|_2 \leq t\}$
* $K = \{(x,t) \space | \space \|x\|_1 \leq t\} : K* = \{(x,t) \space | \space \|x\|_{\infin} \leq t\}$

First three examples are self-dual cones.

Dual cones of proper cones are proper, hence define **generalized inequalities**: 

$y \succcurlyeq _{K^*} 0 \longleftrightarrow y^Tx \geq 0$ for all $x \succcurlyeq_K 0$.

To be non negative in the dual inequality means you make an inner product which is non negative for any vector in the cone.

**Minimum and minimal elements via dual ineuqalities**

**Minimum element w.r.t** $\preccurlyeq_K$: 

$x$ is minimum element of $S$ iff for all $\lambda \succ_{K^*}0$, $x$ is the unique minimizer of $\lambda^Tz$ over $S$. In other words, if you take any dual positive vector and minimize $\lambda ^Tz$ over the set $S$, you always get the minimum element. Minimum elements are unique.

**Minimal element w.r.t.** $\preccurlyeq_K$:

* If $x$ minimizes $\lambda^Tz$ over $S$ for some $\lambda \succ_{K^*}0$, then $x$ is minimal. In other words, if you minimize the $\lambda^Tz$ where $\lambda$ is dual positive, then you are guaranteed the result's minimum.
* If $x$ is a minimal element of a convex set $S$, then there exists a nonzero $\lambda \succcurlyeq_{K^*} 0$ such that minimizes $\lambda^T z$ over $S$. 

**Optimal production frontier**

* Different production methods use different amounts of resources $x \in \text{R}^n$.
* Production set $P$: resource vectors $x$ for all possible production methods.
* Efficient (Pareto optimal) methods correspond to resource vectors $x$ that are minimal w.r.t. $\text{R}_+^n$.

