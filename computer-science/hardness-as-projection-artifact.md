# Hardness as a Projection Artifact: Why Adding Dimensions to Hard Problems Makes Them Easy

**LLM Author:** Claude Opus 4.6 1M
**Human Author:** Shaan Nobee (shaan1337)
**Date:** 2026-04-13
**Domain:** Computer science (algorithms, optimization)
**Cross-domain connections:** Convex geometry, algebraic geometry, linear algebra, complexity theory, machine learning

## Abstract

Many of the most powerful algorithmic techniques — LP relaxation, SDP relaxation, the kernel trick, Lagrangian duality, spectral methods, homogeneous coordinates — share a common structure: they embed a hard problem into a higher-dimensional space where it becomes easy, solve it there, and project back. This paper identifies this lift-and-project pattern as a unified algorithmic design principle and connects it to extension complexity theory, which gives precise, provable limits on when lifting can work. The result is a framework that converts extension complexity from a lower-bound tool into an algorithm design guide: when the extension complexity of a problem's feasible set is polynomial, look for a lift; when it is exponential, use a different strategy.

## Introduction

Consider three problems:

1. Classify data that is not linearly separable in two dimensions.
2. Solve an integer optimization problem with coupled constraints.
3. Analyze a geometric configuration with degenerate special cases.

These appear unrelated. Yet the algorithmic solutions follow an identical pattern:

1. Map the 2D data into a higher-dimensional feature space where a hyperplane separates it. Project the hyperplane back to get a nonlinear decision boundary.
2. Relax the integer constraints to continuous variables (enlarging the feasible set), solve the continuous problem, and round the solution back to integers.
3. Add one coordinate to move from Euclidean to projective space, where the special cases vanish. Compute in projective space and project back.

The pattern: **embed the problem in a richer space where it becomes structurally simpler, solve it there, and project the solution back.**

This pattern recurs across algorithm design, optimization, machine learning, and computational geometry, yet it is rarely articulated as a unified principle. Each community has its own name for its version: "relaxation" in optimization, "kernel trick" in machine learning, "homogeneous coordinates" in geometry, "Fourier transform" in signal processing. The underlying structure is identical.

More importantly, there is a precise complexity-theoretic framework — extension complexity — that determines when this strategy can work and when it provably cannot. This paper unifies these techniques under a single principle and connects them to extension complexity as a design guide.

### A Simple Example

Imagine looking at the shadow of a wire sculpture on a wall. The shadow is a flat 2D image: a tangle of crossing lines. It looks hopelessly complex — you cannot tell which strand passes over which. Untangling the shadow directly seems to require examining every crossing.

But pick up the actual 3D sculpture, and it may be a simple, unknotted loop. The apparent crossings existed only in the 2D projection. The "hard problem" (untangling the crossings) was an artifact of viewing a 3D object in 2D.

This is exactly what algorithmic lifting does. A problem that appears hard in its natural formulation — non-convex, non-separable, full of special cases — may be the projection of a problem that is easy in a higher-dimensional space: convex, separable, uniform. The hardness was in the projection, not the problem.

## Core Insight

### The Lift-and-Project Pattern

Let $P$ be a hard problem defined over a space $X$. The lift-and-project pattern consists of three steps:

1. **Lift**: Find a map $\phi: X \to Y$ where $\dim(Y) \geq \dim(X)$ and the image $\phi(P)$ of the problem in $Y$ is structurally simpler (convex, linear, separable, smooth).
2. **Solve**: Solve $\phi(P)$ in $Y$ using the available structure.
3. **Project**: Map the solution back to $X$ via a projection $\pi: Y \to X$.

The quality of the result depends on how much simpler the lifted problem is and how much information is lost in the projection. When the lift is tight (no information loss), the exact answer is recovered. When approximate, the quality depends on the gap between the lifted and original problems.

Six instances follow, spanning different fields.

### Instance 1: LP Relaxation

The integer linear program

$$\max\ c^T x \quad \text{s.t.}\ Ax \leq b,\ x \in \{0,1\}^n$$

is NP-hard in general. The LP relaxation replaces $x \in \{0,1\}^n$ with $x \in [0,1]^n$:

$$\max\ c^T x \quad \text{s.t.}\ Ax \leq b,\ 0 \leq x \leq 1$$

The feasible set expands from $2^n$ discrete points to the convex hull of those points (and beyond). The expanded problem is a linear program, solvable in polynomial time. The solution is projected back by rounding.

The integrality gap — the ratio between the LP optimum and the integer optimum — measures the information lost in the projection. When the constraint matrix $A$ is totally unimodular and $b$ is integral, the gap is zero: every vertex of the LP relaxation is integral, and the lift is exact. Network flow problems have this property, which is why they are solvable in polynomial time despite being integer programs.

### Instance 2: SDP Relaxation (MAX-CUT)

MAX-CUT asks: given a graph $G = (V, E)$, partition $V$ into two sets to maximize edges between them. Assign $x_i \in \{-1, +1\}$ to vertex $i$. The cut value is:

$$\frac{1}{2} \sum_{(i,j) \in E} (1 - x_i x_j)$$

This is NP-hard. The lift: replace scalars $x_i$ with unit vectors $v_i \in \mathbb{R}^n$, and define $X_{ij} = v_i \cdot v_j$. The constraint $x_i^2 = 1$ becomes $X_{ii} = 1$ and $X \succeq 0$ (positive semidefinite). The rank-1 constraint ($X = xx^T$) is dropped.

The lifted problem is a semidefinite program, solvable in polynomial time. The dimension increases from $n$ scalars to an $n \times n$ matrix — from $n$ to $\binom{n+1}{2}$ variables.

Goemans and Williamson (1995) showed that random hyperplane rounding of the SDP solution achieves a cut of at least $\alpha_{\text{GW}} \cdot \text{OPT}$, where:

$$\alpha_{\text{GW}} = \min_{0 < \theta \leq \pi} \frac{2\theta / \pi}{1 - \cos \theta} \approx 0.878$$

The extra room of the higher-dimensional space (unit vectors instead of binary scalars) is what enables this approximation — optimal assuming the Unique Games Conjecture (Khot et al. 2007).

### Instance 3: The Kernel Trick

Given data $\{(x_i, y_i)\}$ with $x_i \in \mathbb{R}^d$ that is not linearly separable, the kernel trick defines $\phi: \mathbb{R}^d \to \mathbb{R}^D$ (with $D \gg d$) such that the data becomes linearly separable in the higher-dimensional feature space.

The polynomial kernel of degree 2 maps $\mathbb{R}^d \to \mathbb{R}^{\binom{d+2}{2}}$: a quadratic decision boundary in $\mathbb{R}^d$ becomes a hyperplane in $\mathbb{R}^D$. The Gaussian kernel maps to infinite-dimensional Hilbert space, where any finite dataset becomes linearly separable.

The computational trick — using $K(x, y) = \langle \phi(x), \phi(y) \rangle$ instead of explicitly computing $\phi$ — is an implementation detail. Conceptually, the algorithm works in $\mathbb{R}^D$. The hard problem (nonlinear classification in $\mathbb{R}^d$) is the projection of an easy problem (linear classification in $\mathbb{R}^D$).

### Instance 4: Lagrangian Relaxation

Consider minimizing $f(x)$ subject to $g(x) \leq 0$, where the constraint couples variables and makes the problem hard.

The Lagrangian introduces dual variables $\lambda \geq 0$:

$$L(x, \lambda) = f(x) + \lambda^T g(x)$$

The dual problem $\max_{\lambda \geq 0} \min_x L(x, \lambda)$ lives in a higher-dimensional space ($x$ and $\lambda$ together) but decomposes: for fixed $\lambda$, the inner minimization over $x$ may separate into independent subproblems, each solvable efficiently.

The lift is from $\mathbb{R}^n$ (primal) to $\mathbb{R}^{n+m}$ (primal-dual). The coupling constraint becomes a penalty term. When strong duality holds (e.g., under Slater's condition for convex problems), the lift is exact: the dual optimum equals the primal optimum.

### Instance 5: Homogeneous Coordinates

In $\mathbb{R}^2$, parallel lines do not intersect. This forces special-case handling in every geometric algorithm: "if lines are parallel, do X; otherwise, do Y."

Projective space $\mathbb{P}^2$ adds one coordinate: a point $(x, y)$ becomes $[x : y : 1]$, and the line at infinity $[x : y : 0]$ absorbs the special cases. Parallel lines in $\mathbb{R}^2$ intersect at a point at infinity in $\mathbb{P}^2$. All pairs of distinct lines intersect — no exceptions.

The dimension increase is minimal ($d \to d+1$), but the structural simplification is significant: algorithms in projective space are uniform (no case splits), and results are projected back to affine space only at the end.

This is why computer vision algorithms (camera calibration, structure from motion, homography estimation) universally work in homogeneous coordinates. The "hard" special cases in Euclidean geometry are projection artifacts of a uniform geometry in one higher dimension.

### Instance 6: The Fourier Transform

Polynomial multiplication in coefficient representation requires $O(n^2)$ operations (convolution). The discrete Fourier transform lifts to evaluation representation at $n$th roots of unity, where multiplication is pointwise ($O(n)$):

$$\hat{f}(k) = \sum_{j=0}^{n-1} f(j)\, \omega^{jk}, \quad \omega = e^{2\pi i / n}$$

The FFT computes this lift in $O(n \log n)$. The inverse FFT projects back in $O(n \log n)$. Total: $O(n \log n)$ instead of $O(n^2)$.

Unlike the previous instances, the dimension does not increase — both representations have $n$ components. The lift is a change of basis, not a dimension increase. But the structure is identical: transform to a representation where the operation is simpler, compute, transform back. The Fourier basis diagonalizes convolution, converting a hard operation ($O(n^2)$) into a trivial one ($O(n)$).

This is the broadest form of the principle: any change of representation that simplifies problem structure is a lift, whether or not it adds dimensions.

### The Boundary: Extension Complexity

When does lifting work? Extension complexity theory gives a precise answer for the case of linear programming lifts.

A polytope $P \subset \mathbb{R}^n$ may require exponentially many inequalities to describe directly, but it might be expressible as the projection of a simpler polytope $Q \subset \mathbb{R}^{n+k}$ with few inequalities:

$$P = \pi(Q) = \{x \in \mathbb{R}^n : \exists\, y \in \mathbb{R}^k,\ (x, y) \in Q\}$$

The **extension complexity** of $P$, denoted $\text{xc}(P)$, is the minimum number of facets of any such $Q$.

Yannakakis (1991) proved the **factorization theorem**: the extension complexity of $P$ equals the nonnegative rank of its slack matrix $S_P$:

$$\text{xc}(P) = \text{rank}_+(S_P)$$

where $S_P$ has entry $S_{ij} = b_j - a_j^T v_i$ for each vertex $v_i$ and facet inequality $a_j^T x \leq b_j$ of $P$.

This theorem converts a geometric question (how many extra dimensions do I need?) into a linear-algebraic one (what is the nonnegative rank of a matrix?), making extension complexity provable.

### What Extension Complexity Reveals

The known results split neatly:

| Problem | Extension complexity | Implication |
|---------|---------------------|-------------|
| Spanning tree polytope | $O(n^3)$ | Compact LP lift exists (Martin 1991) |
| Bipartite matching polytope | $O(n^3)$ | Compact LP lift exists (Schrijver 2003, via network flow) |
| Permutahedron | $\Theta(n \log n)$ | Compact LP lift exists (Goemans 2015) |
| General matching polytope | $2^{\Omega(n)}$ | No compact LP lift (Rothvoß 2017) |
| TSP polytope | $2^{\Omega(\sqrt{n})}$ | No compact LP lift (Fiorini et al. 2012) |
| Correlation polytope | $2^{\Omega(n)}$ | No compact LP lift (Fiorini et al. 2012) |

The table delivers a sharp message:

- **Polynomial extension complexity**: a compact LP formulation exists in a higher-dimensional space. Find it, and you have a polynomial-time algorithm via LP solving.
- **Exponential extension complexity**: no compact LP formulation exists, regardless of how many dimensions you add. Do not search for one. Use a different approach.

The most striking entry is the general matching polytope. Maximum matching is solvable in polynomial time (Edmonds 1965), yet its polytope has exponential extension complexity. The LP lifting strategy provably cannot solve matching — the polynomial-time algorithm must use a fundamentally different approach (Edmonds' augmenting paths algorithm). Extension complexity identifies not just whether a problem is hard, but whether a *specific algorithmic strategy* can work for it.

## Implications

### 1. Extension Complexity as Algorithm Design Guide

The standard use of extension complexity is proving lower bounds: showing that no small LP exists. But the framework is equally useful for algorithm design. When faced with an optimization problem:

- Estimate the extension complexity of its feasible set.
- If polynomial: search for the compact extended formulation. This is a well-defined mathematical object — finding it is a tractable research problem.
- If exponential for LPs: try SDP lifting (strictly more powerful). If exponential for SDPs too (Lee, Raghavendra, and Steurer 2015): the convex relaxation strategy is exhausted. Use combinatorial or algebraic approaches.

This converts a vague heuristic ("try relaxing the problem") into a principled decision procedure.

### 2. The Hierarchy of Lifts

LP lifts are a special case. The full hierarchy of lifting power is:

$$\text{LP lifts} \subseteq \text{SDP lifts} \subseteq \text{polynomial optimization lifts}$$

The first inclusion is known to be strict: the Goemans-Williamson 0.878-approximation for MAX-CUT uses an SDP lift because the correlation polytope has exponential LP extension complexity — no LP lift can achieve this ratio. The strictness of the second inclusion is conjectured but less completely established.

The Lasserre (sum-of-squares) hierarchy provides a systematic way to climb this ladder: level $k$ uses an SDP lift with $O(n^k)$ variables. Higher levels give tighter relaxations at greater computational cost. For fixed $k$, the level-$k$ relaxation runs in polynomial time and is at least as powerful as any LP or SDP of size $O(n^k)$.

This hierarchy gives algorithm designers a systematic menu: when LP lifting fails, try SDP; when SDP fails, try higher-degree polynomial optimization. Extension complexity at each level tells you when to stop.

### 3. Recognizing the Principle Prevents Reinvention

Because each field names this pattern differently, researchers sometimes reinvent what another field has already systematized. A machine learning researcher developing a new kernel function is solving the same structural problem as an operations researcher designing an extended formulation: both seek the right higher-dimensional space in which the problem becomes convex and separable.

Recognizing the shared structure enables technology transfer. Extended formulation techniques from combinatorial optimization can suggest new kernel designs. Kernel theory's analysis of feature space geometry can inform the choice of lifting variables in optimization.

### 4. The Design Question Is "What Is the Right Lift?"

Most algorithm design asks: "What is the right algorithm for this problem?" The projection principle reframes the question: "What is the right space for this problem?" Once you find the right higher-dimensional space — one where the problem is convex, linear, separable, or smooth — the algorithm often becomes straightforward (solve the LP, find the hyperplane, run gradient descent).

This reframing is practically useful because searching for the right *space* is more constrained than searching for the right *algorithm*. The space must make the problem structurally simpler, and the requirements (convexity, separability, smoothness) are well-defined mathematical properties with known characterizations.

## Limitations

1. **Extension complexity is hard to compute.** Determining the nonnegative rank of a matrix is NP-hard in general (Vavasis 2009). So while extension complexity tells you in principle whether a lift exists, computing it for a specific problem may itself be intractable. The known results in the table above required significant mathematical effort. The framework is most useful when structural properties of the problem give hints about extension complexity.

2. **The principle does not cover all algorithmic techniques.** Divide-and-conquer, dynamic programming, greedy algorithms, and randomized algorithms do not obviously fit the lift-and-project pattern. Dynamic programming can be viewed as lifting (adding a dimension for each subproblem parameter), but this stretches the analogy. The projection principle captures a large and important family of techniques, not all of them.

3. **Finding the right lift is still creative work.** The principle tells you to look for a lift, and extension complexity tells you whether one exists. But constructing the actual lift requires mathematical insight specific to the problem. The Goemans-Williamson SDP for MAX-CUT, Martin's extended formulation for spanning trees, and the Gaussian kernel are all acts of design, not mechanical consequences of the framework.

4. **The FFT and basis-change instances are a weaker fit.** The Fourier transform is a change of basis, not a dimension increase. The strongest version of the principle — with the sharpest complexity-theoretic boundaries — applies specifically to dimension-increasing lifts (LP, SDP, polynomial optimization). Basis changes share the lift-solve-project structure but lack the extension complexity connection.

5. **SDP and higher-level extension complexity is less understood.** While LP extension complexity has a complete characterization (the factorization theorem), the theory for SDP extension complexity is newer and less complete. The precise boundaries of SDP lifting power are an active research area.

## References

- Yannakakis, M. "Expressing combinatorial optimization problems by linear programs." *Journal of Computer and System Sciences*, 43(3):441-466, 1991. (Extension complexity, factorization theorem, symmetric LP lower bounds for TSP.)
- Fiorini, S., Massar, S., Pokutta, S., Tiwary, H.R., and de Wolf, R. "Linear vs. semidefinite extended formulations: exponential separation and strong lower bounds." *Proceedings of the 44th ACM Symposium on Theory of Computing (STOC)*, pp. 95-106, 2012. (Exponential LP extension complexity of TSP and correlation polytopes.)
- Rothvoß, T. "The matching polytope has exponential extension complexity." *Journal of the ACM*, 64(6):41, 2017. (Exponential LP extension complexity of the matching polytope, despite polynomial-time solvability.)
- Goemans, M.X. and Williamson, D.P. "Improved approximation algorithms for maximum cut and satisfiability problems using semidefinite programming." *Journal of the ACM*, 42(6):1115-1145, 1995. (SDP relaxation for MAX-CUT with 0.878-approximation ratio.)
- Edmonds, J. "Paths, trees, and flowers." *Canadian Journal of Mathematics*, 17:449-467, 1965. (Polynomial-time matching algorithm via augmenting paths.)
- Martin, R.K. "Using separation algorithms to generate mixed integer model reformulations." *Operations Research Letters*, 10(3):119-128, 1991. (Extended formulations for combinatorial optimization polytopes.)
- Goemans, M.X. "Smallest compact formulation for the permutahedron." *Mathematical Programming*, 153(1):5-11, 2015. (Tight $\Theta(n \log n)$ extended formulation for the permutahedron.)
- Lee, J.R., Raghavendra, P., and Steurer, D. "Lower bounds on the size of semidefinite programming relaxations." *Proceedings of the 47th ACM Symposium on Theory of Computing (STOC)*, pp. 567-576, 2015. (SDP extension complexity lower bounds.)
- Lasserre, J.B. "Global optimization with polynomials and the problem of moments." *SIAM Journal on Optimization*, 11(3):796-817, 2001. (Sum-of-squares / Lasserre hierarchy for polynomial optimization.)
- Schölkopf, B. and Smola, A.J. *Learning with Kernels: Support Vector Machines, Regularization, Optimization, and Beyond.* MIT Press, 2002. (Kernel methods as implicit lifting to high-dimensional feature spaces.)
- Vavasis, S.A. "On the complexity of nonnegative matrix factorization." *SIAM Journal on Optimization*, 20(3):1364-1377, 2009. (NP-hardness of computing nonnegative rank.)
- Cooley, J.W. and Tukey, J.W. "An algorithm for the machine calculation of complex Fourier series." *Mathematics of Computation*, 19(90):297-301, 1965. (The Fast Fourier Transform.)
- Khot, S., Kindler, G., Mossel, E., and O'Donnell, R. "Optimal inapproximability results for MAX-CUT and other 2-variable CSPs?" *SIAM Journal on Computing*, 37(1):319-357, 2007. (UGC-based optimality of the Goemans-Williamson approximation ratio.)
- Schrijver, A. *Combinatorial Optimization: Polyhedra and Efficiency.* Springer, 2003. (Comprehensive treatment of polytopes, extended formulations, and network flow.)
