---
title: Kantorovich inequality
description: Proofs of the Kantorovich inequality.
toc: true
authors: [ragonneau]
tags:
categories:
series: [Algebra]
date: 2022-01-04T22:45:45+08:00
featuredImage:
draft: false
---

Let $A \in \mathbb{R}^{n \times n}$ be a given symmetric positive definite matrix and denote its eigenvalues $\lambda_1 \le \lambda_2 \le \dots \le \lambda_n$.
The Kantorovich inequality states that for all vector $x \in \mathbb{R}^n$ of unit norm, we have
$$ \langle x, A x \rangle \langle x, A^{-1} x \rangle \le \frac{(\lambda_1 + \lambda_n)^2}{4 \lambda_1 \lambda_n}.$$
Such an inequality is widely used in convergence analysis (e.g., the convergence rate of the [steepest descent method](https://en.wikipedia.org/wiki/Gradient_descent) can be derived from the Kantorovich inequality).
## A proof based on probability theory

We first state three lemmas on which we will base our proof.

> **Lemma 1.**
> Let $X$ and $Y$ be two jointly distributed real-valued random variables with finite second-order moments.
> Then
> $$\mathbb{E}[X] \mathbb{E}[Y] \le \mathbb{E}[XY] + \sqrt{\operatorname{Var}[X] \operatorname{Var}[Y]}.$$

*Proof.* The [Cauchy-Schwarz inequality](https://en.wikipedia.org/wiki/Cauchy-Schwarz_inequality) provides
<div>
    \[\begin{aligned}
        \operatorname{Var}[X] \operatorname{Var}[Y]
            & = \mathbb{E}[(X - \mathbb{E}[X])^2] \mathbb{E}[(Y - \mathbb{E}[Y])^2] \\
            & \ge \mathbb{E}[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])]^2 \\
            & = \operatorname{Cov}[X, Y]^2.
    \end{aligned}\]
</div>
The result follows $\operatorname{Cov}[X, Y] = \mathbb{E}[XY] - \mathbb{E}[X] \mathbb{E}[Y]$.

> **Lemma 2.** *(Popoviciu’s inequality)*
> Let $X$ be a real-valued random variable taking values in $[\alpha, \beta]$, with $\alpha \le \beta$.
> Then
> $$\operatorname{Var}[X] \le \frac{(\beta - \alpha)^2}{4}.$$

*Proof.* Let $\varphi$ be the univariate function defined by $\varphi(t) = \mathbb{E}[(X - t)^2]$.
It easily reaches its minimum at $t = \mathbb{E}[X]$, so that
$$\operatorname{Var}[X] = \varphi(\mathbb{E}[X]) \le \varphi \bigg(\frac{\alpha + \beta}{2}\bigg) = \frac{\mathbb{E}[(2X - \alpha - \beta)^2]}{4}.$$
Remarking that $X - \alpha \ge 0$ and $X - \beta \le 0$, we thus have
$$\operatorname{Var}[X] \le \frac{\mathbb{E}[(X - \alpha - (X - \beta))^2]}{4} = \frac{(\beta - \alpha)^2}{4}.$$

> **Lemma 3.**
> Let $X$ be a real-valued random variable taking values in $[\alpha, \beta]$, with $0 < \alpha \le \beta$.
> Then
> $$\mathbb{E}[X] \mathbb{E}[X^{-1}] \le \frac{(\alpha + \beta)^2}{4 \alpha \beta}.$$

*Proof.* Lemmas 1 and 2 together provide
<div>
    \[\begin{aligned}
        \mathbb{E}[X] \mathbb{E}[X^{-1}]
            & \le \mathbb{E}[XX^{-1}] + \sqrt{\operatorname{Var}[X] \operatorname{Var}[X^{-1}]} \\
            & \le 1 + \sqrt{\frac{(\beta - \alpha)^2 (\alpha^{-1} - \beta^{-1})^2}{16}} \\
            & = \frac{(\alpha + \beta)^2}{4 \alpha \beta}.
    \end{aligned}\]
</div>

We are now ready to prove the Kantorovich inequality.
We let $x \in \mathbb{R}^n$ be any vector of unit norm.
Since $A$ is symmetric positive definite, it admits an [eigendecomposition](https://en.wikipedia.org/wiki/Eigendecomposition_of_a_matrix) $A = Q \Lambda Q^{\mathsf{T}}$ with $Q \in \mathbb{R}^{n \times n}$ an orthogonal matrix and $\Lambda = \operatorname{diag} \\{ \lambda_i \\}_{i = 1, 2, \dots, n}$.
We then have
$$x^{\ast} A x = \sum\_{i = 1}^n \lambda_i v_i^2 \quad \text{and} \quad x^{\ast} A^{-1} x = \sum\_{i = 1}^n \lambda_i^{-1} v_i^2,$$
where $v_i$ denotes the $i$th component of $Q^{\mathsf{T}} x$.
Let $X$ the any random variable that takes the value $\lambda_i$ with probability $v_i^2$ for $i \in \\{ 1, 2, \dots, n \\}$.
Since $X$ clearly takes its values in $[\lambda_1, \lambda_n]$, according to Lemma 3, we have
$$\langle x, A x \rangle \langle x, A^{-1} x \rangle = \mathbb{E}[X] \mathbb{E}[X^{-1}] \le \frac{(\lambda_1 + \lambda_n)^2}{4 \lambda_1 \lambda_n},$$
which concludes our proof of the Kantorovich inequality based on probability theory.
