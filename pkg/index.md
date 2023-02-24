<!-- index.md is generated from index.Rmd. Please edit that file and run knitr::knit("index.Rmd") -->



# Extended Formulas in R

Infrastructure for extended formulas in R with multiple parts on the
right-hand side and/or multiple responses on the left-hand side.


```r
## extended Formula with 2 right-hand sides for mtcars data
library("Formula")
F <- Formula(log(mpg) ~ disp | factor(vs))
mf <- model.frame(f, data = head(mtcars, 3))

## extract response and both regressor matrices from model frame
model.response(mf)
#>     Mazda RX4 Mazda RX4 Wag    Datsun 710 
#>      3.044522      3.044522      3.126761
model.matrix(F, data = mf, rhs = 1)
#>               (Intercept) disp
#> Mazda RX4               1  160
#> Mazda RX4 Wag           1  160
#> Datsun 710              1  108
#> attr(,"assign")
#> [1] 0 1
model.matrix(F, data = mf, rhs = 2)
#>               (Intercept) factor(vs)1
#> Mazda RX4               1           0
#> Mazda RX4 Wag           1           0
#> Datsun 710              1           1
#> attr(,"assign")
#> [1] 0 1
#> attr(,"contrasts")
#> attr(,"contrasts")$`factor(vs)`
#> [1] "contr.treatment"
```
