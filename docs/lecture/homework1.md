# Exercise 1

## Distance between hyperplanes

The distance between the two parallel hyperplanes $\{ x \in \mathbf{R}^n~|~a^T x = b_1 \}$ and $\{ x \in \mathbf{R}^n~|~a^T x = b_2 \}$ is also the distance between the two points $x_1$ and $x_2$ where the hyperplane intersects the line through the origin and parallel to the normal vector $a$. These two points are $x_1 = (b1/\|a\|_2^2)a$ and $x_2= (b2/\|a\|_2^2)a$. So the distance is $\|x_1-x_2\|_2 = |b_1-b_2| / \|a\|_2$

## Voronoi description of a halfspace

Let $a$ and $b$ be distinct points in $\text{R}^n$ and consider the set of points that are closer (in Euclidean norm) to $a$ than $b$ , i.e., $\mathcal{C} = \{x \;|\; \|x-a\|_2 \leq \|x-b\|_2 \}$. Characterize the set $C$ as a halfspace. 

Since a norm is always nonnegative, we have $\|x-a\|_2 \leq \|x-b\|_2$ if and only if $\|x-a\|_2^2 \leq \|x-b\|_2^2$, so
$$
\begin{aligned}
\|x-a\|_2^2 \leq \|x-b\|_2^2 &\longleftrightarrow (x-a)^T(x-a) \leq (x-b)^T(x-b)\\
&\longleftrightarrow x^Tx-2a^Tx + a^Ta \leq x^Tx - 2b^Tx + b^Tb\\
&\longleftrightarrow 2(b-a)^Tx \leq b^Tb - a^Ta
\end{aligned}
$$
Therefore, the set is a halfspace. Take $c=2(b-a)$ and $d=b^Tb-a^Ta$, we have $cx \leq d$. 

This makes geometric sense: the points that are equidistant to $a$ and $b$ are given by a hyperplane whose normal is in the direction $b-a$.

## Common convex sets

Some of the common convex sets:

1. A slab, i.e., a set of the form $\{ x \in \mathbf{R}^n \;|\; \alpha \leq  a^Tx \leq \beta \}$. It's an intersection of two halfspaces.
2. A rectangle, i.e., a set of the form $\{ x \in \mathbf{R}^n \;|\; \alpha_i \leq x_i \leq \beta_i,~i=1,\ldots, n \}$. A rectangle is sometimes called a hyperrectangle when $n>2$. a rectangle is a convex set and a polyhedron because it is a finite intersection of halfspaces.
3. A wedge, i.e., $\{x \in \mathbf{R}^n \;|\; a_1^Tx \leq b_1,~a_2^Tx \leq b_2\}$. It's an intersection of two halfspaces, and also a polyhedron. It's a cone if $b_1=0$ and $b_2=0$.
4. The set of points closer to a given point than a given set, i.e., $\{ x \;|\; \| x- x_0 \|_2 \leq \| x-y\|_2~\mbox{for all}~y \in S\}$, and $\mathbf{dist}(x,S) = \inf \{ \|x-z\|_2 \;|\; z \in S\}$. It can be expressed as $\cap_{u\in S} \{x | \|x-x_0\|_2 \leq \|x-y\|_2\}$, i.e., an intersection of halfspaces. (For fixed $y$, the set $\{x | \|x-x_0\|_2 \leq \|x-y\|_2\}$ is a halfspace).

## Some sets of probability distributions

Let $x$ be a real-valued random variable with $\text{prob}(x=a_i)=p_i, i=1,...,n$, where $a_1 < a_2 < ...< a_n$. Of course $p \in \text{R}^n$ lies in the standard probability simplex $P = \{p\;|\; \mathbf{1}^Tp=1, p \succeq 0\}$. All of the following conditions are convex in $p$ (That is, for all of the following conditions, the set of $p\in P$ satisfies the condition convex)

Notice that $p_i \geq 0, i = 1,...,n$, defines halfspaces, and $\sum_{i=1}^n p_i =1$ defines a hyperplane, so $P$ is a polyhedron. The followings constraints are linear inequalities in the probabilities $p_i$.

1. $\alpha \leq \mathbf{E} f(x) \leq \beta$, where $\mathbf{E} f(x)$ is the expected value of $f(x)$, i.e., $\mathbf{E}f(x)=\sum^n_{i=1} p_i f(a_i)$. (The function $f: \mathbf{R} \rightarrow \mathbf{R}$ is given.)

   Therefore, the constraint is equivalent to two linear inequalities $\alpha \leq \sum^n_{i=1} p_i f(a_i) \leq \beta$.

2. $\mathbf{prob} ( x> \alpha ) \leq \beta$. Since $\mathbf{prob} ( x> \alpha ) = \sum_{i:a_i\leq \alpha} p_i$, the constraint is equivalent to a linear inequality $\sum_{i:a_i\leq \alpha} p_i \leq \beta$.

3. $\mathbf{E} |x^3| \leq \alpha \mathbf{E} |x|$. The constraint is equivalent to a linear inequality $\sum^n_{i=1}p_i (|a_i^3| - \alpha |a_i|) \leq 0$.

4. $\mathbf{E} x^2  \leq \alpha$. The constraint is equivalent to a linear inequality $\sum^n_{i=1}p_ia_i^2 \leq \alpha$.

## Positive semidefinite cones

For $n=1,2,3$. Give an explicit description of the positive semidefinite cone $S_+^n$, in terms of the matrix coefficients and ordinary inequalities, for $n=1,2,3$. To describe a general element of $S^n$, for $n=1,2,3$, use the notation $x_1, \begin{bmatrix}x_1 & x_2\\x_2 & x_3\end{bmatrix}, \begin{bmatrix}x_1 & x_2 & x_3\\x_2 & x_4 & x_5 \\ x_3 & x_5 & x_6 \end{bmatrix}$.

A symmetric matrix $X$ is positive semidefinite if an only if all principal minors (determinants of symmetric submatrices) are non-negative. For $n=1$, the condition is just $x_1 \geq 0$. For $n=2$, the condition is $x_1 \geq 0, x_3 \geq 0, x_1x_3 - x_2^2 \geq 0$. For $n=3$, the condition is $x_1 \geq 0, x_4 \geq 0, x_6 \geq 0, x_1x_4-x_2^2 \geq 0, x_4x_6 - x_5^2 \geq 0, x_1x_6-x_3^2 \geq 0, x_1x_4x_6+2x_2x_3x_5-x_1x_5^2-x_6x_2^2-x_4x_3^2 \geq 0$.

## Dual cones

1. The dual cone of $K = \{0\} \subseteq \mathbf{R}^2$ is $K^* = \mathbf{R}^2$. 
   $$
   \begin{aligned}
   K^* &= \{y|y^Tx \geq 0 \text{ for all } x \in K\} \\
   &=\{y|y^T0 \geq 0\}\\
   &= \mathbf{R}^2
   \end{aligned}
   $$

2. The dual cone of $K = \mathbf{R}^2$ is $K^* = \{ 0 \}$.

   The only value of $y\in \mathbf{R}^2$ is $y=0$ for which $y^Tx \geq 0$ for all $x\in \mathbf{R}^2$.

3. The dual cone of $K = \{(x,y) \mid |x| \leq y \}$ is $K^* = \{(x,y) \mid |x| \leq y \}$.

   This cone is self-dual.

4. The dual cone of $K = \{(x,y) \mid x+y = 0 \}$ is $K^* = \{ (x,y) \mid x - y = 0 \}$.

   $K^* = \{(x_1,x_2) | x_1-x_2=0\}$. Here $K$ is a line, and $K^*$ is the line orthogonal to it.
