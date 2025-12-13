---
layout: post
title: Notes on Functional Analysis
---

# What is functional analysis?

Functional analysis is the study of vector spaces of functions, equipped with norms, inner products, and topologies.

It's like linear algebra, but multidimentsional.

# Why do we study functional analysis?

We want to solve PDEs, variational problems, approximation problems, etc. However, functions are too big to handle, like vectors in $ \mathbb{R}^n$. So, we give them **structure** that generalizes familiar notions from finite dimensions.


# Normed Vector Spaces
What: Vector spaces with a norm.

Why: We need a way to measure size/distance of functions (since PDE solutions are functions, not numbers).

A normed vector space $(X, \|\cdot \|)$. is:
- A vector space $X$
- Has a norm $\|\cdot \|: X \to [0, \infty)$, satisfying
    1. $\| x \| = 0 \iff x = 0,$
    2. $\|\alpha x  \| = \| \alpha \|\|x\|$
    3. $\| x + y \| = \|x\| + \|y\|$

Application: When you approximate PDE solutions with finite elements, you need completeness to ensure the limiting function is still a valid solution.

# Banach Spaces
A Banach space = a complete normed vector space.
"Complete" = every Cauchy sequence converges in the space



# Inner Product Space and Hilbert spaces
What: Banach spaces with an inner product.

Why: Inner products give you geometry, lengths, angles, orthogonality.

An inner product space $(H, <\cdot ,  \cdot>)$:
- $<x,y> \in \mathbb{R}$
- linear in first slot
- symmetric
- positive definite
- norm: $\|x\| = \sqrt{<x,x>}$

if complete, then this inner product space

Hilbert spaces = “infinite-dimensional Euclidean spaces”.

Application: The heat equation or Schrödinger equation naturally live in Hilbert spaces because energy/orthogonality matter. Hilbert space structure is crucial for the variational (weak) formulation of PDEs.

# Linear Functionals and Dual Spaces
What: A functional is a “number-valued linear map”

$$F: X \to \mathbb{R}$$

Why: Many PDEs and optimization problems are expressed in terms of duality. Weak derivatives are also defined using duality.

Used for: Weak formulations, optimization, and adjoints.

## Linear functional


## Dual space

Weak derivative: we say v is the derivative of u if
$$\int u \phi' = - \int v \phi$$
for all test functions $\phi$. This is a duality statement. 
# Operators 

## Linear operator
What: Linear maps between spaces.

Why: PDEs are operator equations

A linear operator 
$$T: X \to Y$$

## Bounded operator
$$\|Tx\| \leq C\|x\|$$

These operators generalize matrices (what does this mean)

# Convergence
In finite dimensions, all norms are equivalent. Not true in infinite dimensions!
We have:

- Norm convergence: $$\| x_n - x\| \to 0$$
- Weak convergence: $$x_n \to x \text{ if } F(x_n) $$
- Weak convergence is weaker but often compactness only holds weakly.

This is crucial in Sobolev spaces: PDE solutions often only converge weakly.

# Compactness

What: Compact operators map bounded sequences to sequences with convergent subsequences.

Why: Helps extract convergent subsequences where direct convergence fails.


- Compact operator = maps bounded sets to relatively compact sets.
- In finite dimensions, bounded = compact. Not in infinite.
- Tools like Rellich–Kondrachov theorem (compact Sobolev embedding) rely on this.


-----------------------------------------------------------

Now that you know 
- Normed spaces ($L^p$)
- Hilbert spaces ($L^2$)
- Weak convergence
- Operators

We can define Sobolev spaces as 
$$W^{k,p}(\Omega) = \{ u \in L^{p}: \text{all weak derivatives } D^{\alpha}u \in L^{p}, | \alpha |\leq k\}$$


# Sobolev Spaces

