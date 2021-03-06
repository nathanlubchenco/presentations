---
title       : Understanding Data  
subtitle    : 
author      : Nathan Lubchenco  
job         : Simple Energy 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     :  [bootstrap, quiz, shiny, interactive] # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---
## Topics

1. Standard Deviation
2. Statistical Significance 
3. Linear Regression

--- &twocol

## Standard Deviation
A measure of dispersion of the data

*** =left 
![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1-1.png) 

*** =right
![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png) 

--- .class #id 
## Standard Deviation
If the data is distributed approximately normal then:

* 68% of data is within 1 standard deviation of the mean
* 95% of data is within 2 standard deviations of the mean
* 99% of data is within 3 standard deviations of the mean

![std-dev_graph](assets/img/std_dev.png "Standard Deviation Visualization")

--- .class #id 
## Standard Deviation
### Common Mistake

Not all data is normally distributed

![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3-1.png) 



--- .class #id 
## Standard Deviation
### Use cases

* Filtering Outliers
  * For EE calcs we filter out any day where usage is greater than 4 standard deviations away from the mean

* Detecting Data Descrepencies
  * Data Ingestion -- usage, number of accounts

* Estimating Trends
  * Is this data likely due to a genuine change or is it explainable by noise

--- .class #id 
## Standard Deviation

Monthly Activations for program X
```
Mean: 212
Standard Deviation: 60 
```

* What should we think about a new month that has 
  * 177 activations?
  * 300 activations?
  * 13 activations?


--- .class #id 

![plot of chunk unnamed-chunk-4](assets/fig/unnamed-chunk-4-1.png) 

--- .class #id 
## Statistical Significance

```
Null Hypothesis: 
  Assumption that there is no relationship between variables of interest
```

1. False Positive: 
   - Type I Error 
   - the null hypothesis is true, but we reject it and believe something false
2. False Negative:
   - Type II Error 
   - the null hypothesis is false, but we fail to reject it and do not believe something true

--- .class #id 
## Statistical Significance

In a trial, the null hypothesis is that there is no relationship between the person and the crime:

  What type of error is it if an innocent person is convicted?

  What type of error is it if a guilty person is acquitted? 

--- .class #id 
## Statistical Significance 

* Beyond a reasonable doubt
   - makes false positive less likely
   - conversely, increases the likelihood of false negatives 

* a p-value allows us to control the probability of false positives 
   - by convention the threshold for statistical signficance is set to .05

```
"A p value is not a measure of how right you are, 
or how significant the difference is; 
it’s a measure of how surprised you should be 
if there is no actual difference between the groups, 
but you got data suggesting there is."
```
[statisticsdonewrong](http://www.statisticsdonewrong.com/data-analysis.html)

---  &twocol
## Statistical Significance 

*** =left

![plot of chunk unnamed-chunk-5](assets/fig/unnamed-chunk-5-1.png) 

*** =right

![plot of chunk unnamed-chunk-6](assets/fig/unnamed-chunk-6-1.png) 

--- .class #id 
## Statistical Significance 

### Common Mistake

Confusing statistical significance with practical signficance

A series of A/B tests reveal:  

```
Feature X will, on average, increase a user's pageviews by 3%.
```

```
Feature Y will, on average, decrease a user's energy usage by 3%.
```

Both results are highly statistically significant. (p value < .001) 

Which, if any, results should we care about?

--- .class #id 
## Statistical Significance 

### Common Mistake II

Interpreting results that are not statistically significant as if they still indicate 'something'

```
For program X, we showed energy savings of %0.8,
but the results were not statistically significant.
```

If results are not statistcally significant:
* they are indistinguishable from 0  
* no trend is indicated

It is ok to say that we don't know anything yet.

Yes, this is hard.
* Ask for the why

---  &twocol
## Linear Regression

*** =left

![plot of chunk unnamed-chunk-7](assets/fig/unnamed-chunk-7-1.png) 

*** =right

![plot of chunk unnamed-chunk-8](assets/fig/unnamed-chunk-8-1.png) 

--- &twocol
## Linear Regression

*** =left

![plot of chunk unnamed-chunk-9](assets/fig/unnamed-chunk-9-1.png) 

*** =right

![plot of chunk unnamed-chunk-10](assets/fig/unnamed-chunk-10-1.png) 

--- .class #id 

## Linear Regression
### Some junior high math

Equation for a line:
y = mx + b

m is the slope, b is the y-intercept

### Regression Equation
y = &beta;0 + &beta;1\*hp + _e_ 

&beta;0 is the y-intercept 
&beta;1 is the coefficient of hp 

### Interpreting the coefficient
A one unit change in hp will, on average, 
be associated with a &beta;1 change in mpg.

--- .class #id 

## Linear Regression

```
##                Estimate Std. Error   t value     Pr(>|t|)
## (Intercept) 30.09886054  1.6339210 18.421246 6.642736e-18
## hp          -0.06822828  0.0101193 -6.742389 1.787835e-07
```

--- &twocol
## Linear Regression

*** =left

![plot of chunk unnamed-chunk-12](assets/fig/unnamed-chunk-12-1.png) 

*** =right

![plot of chunk unnamed-chunk-13](assets/fig/unnamed-chunk-13-1.png) 

--- .class #id 
## Prediction is hard

![japan-birth-rate-prediction](assets/img/flowing_data_japan_predictions.png "Birth Rate Predictions")

```
"It's hard to predict the future, especially when humans are involved."
```
[Flowing Data](http://flowingdata.com/2015/01/08/japan-fertility-rate-forecasts-versus-reality/)

--- &twocol 
## Possible Future Topics

*** =left
* Experimental Design
  * The power of randomized control trials
  * Sample Size
  * Selection Bias

* Predicitve Modeling
  * Regression vs Classification Problems
  * Supervised vs Unsupervised Learning
  * Evaluation
  * Training Data / Cross-Validation
  * Simulation as projection

*** =right
* A/B Testing
  * Importance of pre-defined criteria
  * Danger of repeated testing
  * Low Base Rate / Skewed Distribution (eg. conversions)

* Cognitive Biases
  * Framing Effects
  * Anchoring Effects
  * Prospect Theory
  * Paradox of Choice
  * Base Rate Fallacy

