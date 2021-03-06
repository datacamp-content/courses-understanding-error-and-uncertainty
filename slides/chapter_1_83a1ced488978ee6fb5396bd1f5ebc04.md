---
title: Insert title here
key: 83a1ced488978ee6fb5396bd1f5ebc04

---
## How Confident Are You?

```yaml
type: "TitleSlide"
key: "39293ca52c"
```

`@lower_third`

name: Evan Kramer
title: Instructor


`@script`
Hi, I'm Evan Kramer. This lesson will teach you some simple ways to distinguish between two groups using confidence intervals. By the end of this chapter, you should be able to define these terms and use formulas to calculate significant differences between groups.


---
## Explore the Data

```yaml
type: "FullImageSlide"
key: "cce701e15b"
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4139/datasets/76e17596177fa4336c66312f6c9f672a5248a5c8/dc2.PNG)


`@script`
Imagine we have the following data set, which lists actual sales for each of the last 19 days. An analyst on our team also created two sets of predictions using a number of different assumptions (such as whether the economy was improving, if it was sunny outside, etc.). We compared each prediction to the actual value on that day, and we want to determine which set of predictions is more accurate, by comparing to our actual sales data.


---
## Confidence Intervals (CI)

```yaml
type: "FullSlide"
key: "b441ad0dc3"
```

`@part1`
- Ranges of values that contain the true parameter X% of the time {{1}}
    - Example: 95% CI contains the true value 95 of 100 data collections
- Function of three factors {{2}}
    - alpha (confidence level) {{3}}
    - variation in the data (standard deviation) {{4}}
    - number of data points {{5}}


`@script`
Confidence intervals, or CI for short, can help us do just that. They can assess the accuracy of our predictions by estimating the amount of error in the data. 

Confidence intervals are ranges of values that contain the true parameter a certain percentage of the time. When calculating CIs, we specify how much certainty we expect to have. For example, if we collect data 100 different times, a 95% confidence interval will contain the true value 95 of those times.

CIs vary based on three factors: 1) the alpha, or confidence level; 2) the variance of the data, as measured by the standard deviation--or average distance from the average; and 3) the number of observations the data set contains. 

The higher the confidence level, the larger the interval. This should make intuitive sense. A larger range (or interval), gives us more confidence that a given value will fall within it. A typical alpha level is 0.05 for 95% confidence. 

The variation also impacts the size of the confidence interval. Data with more variation requires a larger confidence interval, as we grow less certain that our sample represents all the variation in the true data. 

Finally, a higher number of observations decreases the size of the confidence interval because more data points give us greater predictive power and confidence.


---
## CI Calculations

```yaml
type: "TwoColumns"
key: "02c00250e9"
```

`@part1`
- n = `19` {{1}}
    - `-=COUNT(A2:A20)`{{1}}
- mean = `40` {{2}}
   - `=AVERAGE(A2:A20)` {{2}}
- alpha = `0.05` {{3}}
- standard deviation = `28.35` {{4}}
    - `=STDEV(A2:A20)` {{4}}


`@part2`
![](https://assets.datacamp.com/production/repositories/4139/datasets/2557b5a995df2663f963e3b8b0feeb1776d5aeea/dc4.PNG){{1}}


`@script`
Now let's calculate confidence intervals. Recall that our data set had 19 observations and a mean of 40. Let's set alpha equal to 0.05 for a 95% confidence level. We can use the STDEV formula to calculate the standard deviation of the data as approximately 28.35.


---
## CI Calculations

```yaml
type: "TwoColumns"
key: "b0388610e6"
```

`@part1`
- confidence interval: `=CONFIDENCE(0.05, STDEV(A2:A20), COUNT(A2:A20))` 
- ≈ `12.75` {{1}}


`@part2`
![](https://assets.datacamp.com/production/repositories/4139/datasets/2ba18c5922cef128bcfe9c13f462e4b457b0323f/dc5.PNG)


`@script`
We can put this all together to calculate the confidence interval. Our formula returns a result of approximately 12.75. But how should we use this information?


---
## Know Yo' Bounds

```yaml
type: "FullSlide"
key: "7c114dadbe"
```

`@part1`
- Upper and lower bounds straddle mean {{1}}
    - Upper bound: add half of CI to mean {{2}}
    - Lower bound: subtract half of CI from mean {{3}}
- Average outside of bounds indicates significant differences {{4}}


`@script`
We typically refer to confidence intervals by their upper and lower bounds around the mean. Half of the confidence interval we calculated will lie above the mean, while the other half will fall below it.

Recall that in 95% of repeated samples the true average sales amount will fall between the upper and lower bound. As such, if the mean of our sales predictions falls outside of these bounds, we can say fairly confidently that these predictions differ significantly from reality.


---
## Out of Bounds

```yaml
type: "TwoColumns"
key: "b16cfd0244"
```

`@part1`
- upper bound {{1}}
    - `=AVERAGE(A2:A20) + ` {{2}}
    - `CONFIDENCE(0.05, STDEV(A2:A20), COUNT(A2:A20)` {{3}}
    - `/ 2)`{{4}}
    - `≈ 46.37` {{5}}


`@part2`
![](https://assets.datacamp.com/production/repositories/4139/datasets/dccf89670361ba91c3584364710b74db6c39e639/dc6.PNG) {{5}}


`@script`
Now let's calculate upper and lower confidence interval bounds, starting with the upper. 

We'll start with the average of our sales data.

Then we'll calculate the confidence interval...

... and add half of it to the mean we previously calculated, which gives us an upper bound of approximately 46.37.


---
## Out of Bounds

```yaml
type: "TwoColumns"
key: "de69c06e91"
```

`@part1`
- lower bound
    - `=AVERAGE(A2:A20) - ` {{2}}
    - `CONFIDENCE(0.05, STDEV(A2:A20), COUNT(A2:A20)` {{3}}
    - `/ 2)`{{4}}
    - `≈ 33.63` {{5}}


`@part2`
![](https://assets.datacamp.com/production/repositories/4139/datasets/dccf89670361ba91c3584364710b74db6c39e639/dc6.PNG)


`@script`
Next we'll calculate the lower confidence interval bound. 

Again we start with the average of our sales data.

Then we'll calculate the confidence interval...

... this time **subtracting** half of it from the mean we previously calculated, which gives us a lower bound of approximately 33.63.


---
## Confident Conclusions

```yaml
type: "FullSlide"
key: "d65d047df0"
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4139/datasets/dccf89670361ba91c3584364710b74db6c39e639/dc6.PNG)


`@script`
So what do these results tell us? Well we can see that the mean of the first set of predictions (which is 59.37, stored in cell B22), is outside the bounds of the confidence intervals of our sales data. This suggests these predictions might be outside the realm of normal variation. However, the mean of our analyst's second set of predictions is 42.84 (in cell D22), higher than the mean of our actual sales data but firmly within the bounds of our 95% confidence interval. We can conclude, then, that these predictions are not significantly different from our real data and may be more trustworthy than the first set.


---
## Let's Practice!

```yaml
type: "FinalSlide"
key: "407a6a4d5a"
```

`@script`
This lesson defined confidence intervals and showed you how to calculate them and use upper and lower bounds to determine significant differences. Now let's test your skills!

