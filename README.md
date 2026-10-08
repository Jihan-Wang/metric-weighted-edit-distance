# Metric-Weighted Edit Distance

## Extending OpenAI's Family 121 Framework

This repository shares the manuscript **An Almost-Linear Approximation Scheme for Metric-Weighted Edit Distance** and an independent technical explanation of OpenAI's **An Almost-Linear Approximation Scheme for Edit Distance**, catalogue family 121.

The manuscript adapts the unit-cost refinement framework to arbitrary metric weights. It also retunes the parameters to obtain a sharper explicit expected-work bound. These are separate contributions: the retuning applies to unit costs as well.

This is an independent research repository. It is not an official OpenAI repository.



## Manuscript claim

Let $`x,y`$ be the input strings and let $`N=|x|+|y|`$. Let $`w`$ be a metric on the alphabet augmented with a gap symbol $`\bot`$. Deletion, insertion, and substitution costs are $`w(a,\bot)`$, $`w(\bot,b)`$, and $`w(a,b)`$, respectively. Write $`D=\mathrm{WED}_w(x,y)`$.

For every fixed rational $`\varepsilon>0`$, the manuscript claims a randomized scalar estimator satisfying

```math
\Pr\{D\le\widehat D\le(1+\varepsilon)D\}\ge\frac56,
\qquad
\mathbb E T(N)\le N^{1+O(\log\log\log N/\log\log N)}.
```

The theorem uses constant-time exact queries to a deterministic metric oracle and constant-time exact real arithmetic. Finite binary control and fair random bits are charged. The expected-work bound is unconditional and uniform over positive cost ratios. Constants and the input-size cutoff may depend on the fixed accuracy. The construction uses polynomial workspace and terminates on every random-bit sequence.

This is a theoretical construction with scalar output. The repository does not contain an executable implementation of the approximation algorithm or a formal proof certificate. Component-wise manual audits found no theorem-breaking defect in the checked proof chain under the stated model. Community review remains useful, especially at the interfaces between normalization, seed construction, refinement, and total-work accounting.

## Where the runtime improvement comes from

OpenAI states a fixed-accuracy $`N^{1+o(1)}`$ bound for unit-cost edit distance. Expanding its displayed parameter schedule gives the conservative upper bound

```math
N^{1+O((\log\log\log N)^{-1/4})}.
```

Our sharper explicit bound comes from a different parameter schedule and sharper depth, dimension, and dependency estimates. It also holds for unit costs through the current construction's specialization. The comparison concerns analyzed upper bounds. It does not establish a lower bound on OpenAI's algorithm or global optimality of either schedule. 

## Sources

- [OpenAI, An Almost-Linear Approximation Scheme for Edit Distance, September 24, 2026](https://github.com/openai/math/blob/main/preprints/An-Almost-Linear-Approximation-Scheme-for-Edit-Distance-September-24-2026/paper.pdf).
- [Das, Kipouridis, and Kociumaka, Metric Weighted Edit Distance, arXiv:2609.20796v1](https://arxiv.org/abs/2609.20796v1).
- [Mader, Tavasoli, and Wang, A Strongly Subquadratic Approximation for Weighted Edit Distance over Arbitrary Metrics, arXiv:2609.14873v1](https://arxiv.org/abs/2609.14873v1).

The weighted papers supply related gap-mass, simplification, local-query, and distance-bracketing tools. The manuscript identifies their use separately from its adaptation of OpenAI's refinement. The reading guide is our exposition, not an upstream manuscript or an endorsement by its authors.

## Corrections and discussion

Report of proof issue or suggestion of expository change are welcome. Please identify the document version, section, and exact claim. State the missing implication or counterexample whenever possible.
