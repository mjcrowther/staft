# staft
Flexible parametric accelerated failure time models in Stata

## Installation

Install directly using:

```{stata}
net install staft, from("https://raw.githubusercontent.com/mjcrowther/staft/master/")
```

# References

Crowther MJ, Royston P, Clements M. A flexible parametric accelerated failure time model and the extension to time-dependent acceleration factors. *Biostatistics* 2023;24(3):811-831. https://doi.org/10.1093/biostatistics/kxac009

# Acknowledgements

`staft` generates its restricted cubic spline basis functions with `rcsgen`, written by Paul C. Lambert and available from SSC (`ssc install rcsgen`), which `staft` requires. The file `rcsgen2.ado`, installed with `staft`, is adapted from `rcsgen`.
