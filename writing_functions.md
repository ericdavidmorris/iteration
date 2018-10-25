writing\_functions
================
Eric Morris
10/25/2018

Writing some functions
----------------------

Starting smol

``` r
x = rnorm(25, 5, 3)

(x - mean(x)) / sd(x)
##  [1] -0.50335236  2.12329028 -0.84508857  0.39447144  1.63591648
##  [6] -0.60555519 -0.54014606 -0.87046337  0.18001848 -0.46767359
## [11]  0.22529488 -0.50420442  0.34436925  1.58842453  0.51595100
## [16]  0.75675933  0.05081117  1.03317399  1.29133437 -1.26113116
## [21]  0.04128607 -1.30160491 -1.70770855 -0.96064493 -0.61352816
```

Write a function to compute z scores for a vector

``` r
z_scores = function(x) {
  
  (x - mean(x)) / sd(x)
  
}
```

Check to see if this works

``` r
unif_sample = runif(100)

z_scores(x = unif_sample)
##   [1]  0.737355292 -1.488377332 -0.371035142 -0.240315015 -0.052115586
##   [6] -1.049039760  1.806085023 -0.437770242 -0.751813883  1.525486566
##  [11]  1.286933954  1.483369946 -0.599823408  1.128241059 -1.170609563
##  [16] -0.027052682 -1.689500710 -0.161432745  0.480677967 -0.220619023
##  [21] -0.745815286 -1.285308027  0.630697355  0.878361507 -1.570231073
##  [26]  1.221194571  0.638161462 -1.463041097 -0.056718326  1.501420429
##  [31] -1.076051928 -1.633230223  0.447278291  0.077092149  1.715716705
##  [36] -1.859551532  0.603514550  0.349513162  1.291433150 -0.676729019
##  [41]  0.783216616 -0.002408709  0.518652167 -1.716990438 -1.133391794
##  [46] -1.065052251 -0.533297110 -0.243583918 -0.446147312  1.124311818
##  [51]  0.825352179 -0.202317271  0.080863086 -0.552906257 -1.267670293
##  [56] -0.691357700  0.119176238 -0.495667596 -1.468112228 -0.933552111
##  [61] -1.523888617  0.811426027 -0.106351816  0.948900964  0.542224272
##  [66] -0.063667854 -1.423896371  1.418835499 -0.719895991  1.245103522
##  [71]  0.120491672  1.747273825  1.536967836 -0.593275611  1.496071931
##  [76] -1.623128479  1.132316799 -0.657893051  1.149086280 -0.717464751
##  [81]  0.879794564  0.064500240 -1.337195631 -0.797047205 -0.323504200
##  [86]  1.699659972 -0.464950507  0.107523081  1.048360466  1.112887917
##  [91]  0.502396896  0.207955161 -0.013327326  1.306918277 -1.246244558
##  [96]  0.115200416  1.198794258 -0.541788848  0.365009804 -0.479647513
```

Check some other examples

``` r
z_scores(3)
## [1] NA
z_scores("my name is jeff")
## Warning in mean.default(x): argument is not numeric or logical: returning
## NA
## Error in x - mean(x): non-numeric argument to binary operator
z_scores(iris)
## Warning in mean.default(x): argument is not numeric or logical: returning
## NA
## Warning in Ops.factor(left, right): '-' not meaningful for factors
## Error in is.data.frame(x): (list) object cannot be coerced to type 'double'
z_scores(sample(c(TRUE, FALSE), 25, replace = TRUE))
##  [1] -0.8 -0.8  1.2 -0.8 -0.8 -0.8  1.2  1.2 -0.8  1.2  1.2 -0.8  1.2 -0.8
## [15] -0.8  1.2 -0.8 -0.8  1.2 -0.8 -0.8  1.2 -0.8  1.2 -0.8
```

Put in some checks on inputs for your function...

``` r
z_scores = function(x) {
  
  if (!is.numeric(x)) {
    stop("Argument x should be numeric")
  } else if (length(x) == 1) {
    stop("Z scores cannot be computed for length 1 vectors")
  }
  
  z = mean(x) / sd(x)
  
  z
}
```

New function for mean and SD
----------------------------

``` r
mean_and_sd = function(x) {

  if (!is.numeric(x)) {
    stop("Argument x should be numeric")
  } else if (length(x) == 1) {
    stop("Z scores cannot be computed for length 1 vectors")
  }
  
  tibble(
  mean_x = mean(x),
  sd_x = sd(x)
  )
  
  #c(mean_x, sd_x) 
  
}

mean_and_sd(unif_sample)
## # A tibble: 1 x 2
##   mean_x  sd_x
##    <dbl> <dbl>
## 1  0.507 0.272
```
