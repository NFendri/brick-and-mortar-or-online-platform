# brick-and-mortar-or-online-platform

Optimal timing to switch from a brick-and-mortar store to an online platform, modeled as an
optimal-stopping / HJB variational inequality and solved numerically with Howard's
policy-iteration algorithm.

## The model

A retailer's physical-store popularity `x` declines over time (`dX_t = alpha * X_t dt`,
`alpha < 0`), while the level of available technology `theta` improves via a compound Poisson
jump process. The firm chooses when to pay a one-time cost `I` and switch to an online
platform. The value function `F(theta, x)` solves the HJB variational inequality

    min{ r*F - [pi0(x) + L*F], F - V(theta) } = 0

where `pi0` is the physical-store profit flow, `V(theta)` is the value of switching now, and
`L` is the infinitesimal generator of `(theta, x)`. It's solved via Howard's algorithm,
alternating between a Sylvester-equation solve for the continuation region and a comparison
against the stopping value.

Full derivation and background: [Graduation Project Report](https://nasserfendri.github.io/Graduation-Project-Report.pdf)
(GERAD Laboratory research internship, 2022).

## This repo

`Brick_and_mortar_or_online_platform.ipynb` — a cleaned-up, vectorized reimplementation of
the original Colab notebook, plus a sensitivity analysis reproducing the report's parameter
sweeps (grid step, technology jump size, cost of innovation, profit-flow function) with a
summary table of results. Open in [Google Colab](https://colab.research.google.com/github/NFendri/brick-and-mortar-or-online-platform/blob/main/Brick_and_mortar_or_online_platform.ipynb).
