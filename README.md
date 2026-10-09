# staft

Flexible parametric accelerated failure time models in Stata.

`staft` fits accelerated failure time models in which the baseline is modelled with restricted cubic splines, so that covariates act by accelerating or decelerating time:

    S(t|X) = S0(t exp(-X beta))

## What it fits

- **Baseline:** restricted cubic splines, with knots placed by degrees of freedom or given by the user.
- **Time-dependent effects:** time-dependent acceleration factors, each with its own spline function.
- **Data:** single- or multiple-record and single- or multiple-failure `st` data; weights are taken from `stset`. Factor variables are not currently supported.
- **Predictions:** the linear predictor, hazard, survival and cumulative hazard functions, and the acceleration factor, with confidence intervals or standard errors.

## Requirements

- Stata 15.1 or later
- `stpm2` and `rcsgen`: `ssc install stpm2` and `ssc install rcsgen`

## Installation

Install directly using:

```stata
net install staft, from("https://raw.githubusercontent.com/mjcrowther/staft/master/")
```

## Example

An accelerated failure time model with 3 degrees of freedom for the baseline spline function:

```stata
webuse brcancer, clear
stset rectime, failure(censrec = 1) scale(365.25)
staft hormon, df(3)
```

The options are described in the help file: `help staft`.

## Version

Version 1.2.0 (9 October 2026). Covariates that are constant in the estimation sample, or collinear with a constant and each other, are now omitted with a note, as `streg` does. In earlier versions they were estimated, which changed the fitted model.

Version 1.1.0 (8 October 2026) corrected predictions made after estimation:

- the predicted hazard after `tvc()`, and the standard error of the predicted hazard;
- `level()` is now passed to the confidence intervals of `xb` and `af`;
- `stdp` now returns the prediction and its standard error on the natural scale; `ci` and `stdp` can not be combined.

## References

Crowther MJ, Royston P, Clements M. A flexible parametric accelerated failure time model and the extension to time-dependent acceleration factors. *Biostatistics* 2023;24(3):811-831. https://doi.org/10.1093/biostatistics/kxac009

## Acknowledgements

`staft` generates its restricted cubic spline basis functions with `rcsgen`, written by Paul C. Lambert and available from SSC (`ssc install rcsgen`), which `staft` requires. The file `rcsgen2.ado`, installed with `staft`, is adapted from `rcsgen`.

## Licence

Copyright (c) 2018 Michael J. Crowther.

Released under the MIT License. See [`LICENSE`](LICENSE).
