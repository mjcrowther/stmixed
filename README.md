# stmixed

Multilevel mixed effects parametric survival analysis in Stata.

`stmixed` fits survival models with random effects at one or more levels. It is a wrapper for [`merlin`](https://www.stata-journal.com/article.html?article=st0616): it sets the model up and passes it to `merlin` for estimation, so `merlin` must be installed.

## What it fits

- **Baseline distributions:** exponential, Weibull, Gompertz, generalised gamma, log normal, log logistic, piecewise exponential, Royston-Parmar, restricted cubic splines on the log hazard scale, or a user-defined model.
- **Random effects:** random intercepts and random coefficients, at any number of nested levels, with a choice of covariance structure.
- **Extensions:** time-dependent effects, and relative survival through an expected mortality rate.
- **Predictions:** hazard, survival, cumulative hazard, cumulative incidence, restricted mean survival time and time lost, conditional on the fixed effects only or marginal over the random effects, with confidence intervals.

## Requirements

- Stata 15.1 or later
- `merlin`, version 1.12.0 or later: `ssc install merlin`

## Installation

The latest stable version of `stmixed` can be installed with:

```stata
ssc install stmixed
```

To install directly from this GitHub repository, use:

```stata
net install stmixed, from("https://raw.githubusercontent.com/mjcrowther/stmixed/main/")
```

## Example

A simulated multi-centre trial with 100 centres, fitted with a Weibull baseline and a random intercept for centre:

```stata
use http://fmwww.bc.edu/repec/bocode/s/stmixed_example1, clear
stset stime, f(event=1)
stmixed x1 x2 || centre: , dist(weibull)
```

Further examples are in the help file: `help stmixed`.

## Version

Version 2.2.3 (6 February 2023), the same version as on SSC.

## References

`stmixed` began as the Stata implementation of the methods in:

> Crowther MJ, Look MP, Riley RD. Multilevel mixed effects parametric survival models using adaptive Gauss-Hermite quadrature with application to recurrent events and individual participant data meta-analysis. *Statistics in Medicine* 2014;33(22):3844-3858.

Its later development as a wrapper for `merlin` is described in:

> Crowther MJ. Multilevel mixed effects parametric survival analysis: Estimation, simulation and application. *Stata Journal* 2019;19(4):931-949. (Pre-print: https://arxiv.org/abs/1709.06633)

## Licence

Copyright (C) 2012-2023 Michael J. Crowther.

Released under the GNU General Public License, version 3. See [`LICENSE`](LICENSE).
