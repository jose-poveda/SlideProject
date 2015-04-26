---
title       : Confidence intervals
subtitle    : Material to accompany the shiny app "95% Confidence intervals for the mean"
author      : Jose Poveda
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
--- .class #id 

## Importance of confidence intervals

* It is possible to estimate the value of a certain variable by extracting a sample and computing its mean.

* However, this is a quantity with little use, because it is unlikely the real mean of the population is by chance, the same as the sample mean.

* On the other hand, we know that the sample mean must be close to the population mean.

* With this in mind, and by using statistic tools, we can create an interval in which we can be almost certain the population mean is for any given population.

--- .class #id 

## Definition

* A confidence interval for a parameter is found between L and U by this relation:

``` 
P(L<theta<U) = 1 - alpha
```

Where 1 - alpha is the confidence coefficient. This means, for example if 1 - alpha is 95%, that 95% of the extracted samples mean will be into the limits of L and U.

* There are multiple confidence intervals that are commonly used, by default 95% is selected.

--- .class #id

## Intervals for the mean

The random factor must be introduced. Something to take in consideration is the fact that the population must distribute normally. If that's the case, then the mean should distribute as a t student with n - 1 degrees of freedom:

For example, if our sample mean is 20, our sample standard deviation is 5 and the sample size is 20:


```r
mean1 = 20; sd1 = 5; ss = 20;
lower = mean1 - qt(0.975, ss - 1) * sd1 / sqrt(ss)
upper = mean1 + qt(0.975, ss - 1) * sd1 / sqrt(ss)
print(c(lower, upper))
```

```
## [1] 17.65993 22.34007
```

--- .class #id

## Using the Shiny App

This shiny app computes a 95% confidence interval for any given mean, using a t distribution.

* Sample mean: In this field, introduce the sample mean for your data (any real number).

* Sample standard deviation: In this field, introduce the sample standard deviation for your data (any positive number).

* Sample size: In this field introduce the sample size used to estimate the sample mean and the sample standard deviation (a positive integer).

As mentioned, the computation uses these formulas:
```
Lower limit: mean - t * standard deviation / sqrt(sample size)
Upper limit: mean + t * standard deviation / sqrt(sample size)
```

Where t is calculated by:
```
qt(0.975, sample size - 1)
```

