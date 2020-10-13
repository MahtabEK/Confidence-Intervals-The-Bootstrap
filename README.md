# Confidence-Intervals-The-Bootstrap

**Section 1**

**Part 1:**
We know that a 199(1−𝛼)%  confidence interval for the mean is 𝑥¯±𝑡1−𝛼/2,𝑛−1𝜎̂ 𝑛⎯⎯√

Where  𝑡1−𝛼/2,𝑛−1  is the appropiorate quantile of a Student's t distribution with 𝑛−1 degrees of freedom. When  𝛼=0.05  and when  𝑛  is big enough,  𝑡1−𝛼/2,𝑛−1≈1.96.

Here, I wrote a function called confidence_interval which takes as it's argument an array of data called data and returns two things:
- An estimated mean of data, and 
- The lower and upper bounds of the 95% confidence interval for the mean of data. These are returned in a numpy array of shape (2,)

**Part 2:**
The "95% confidence interval" is named so because the long term relative frequency of these estimtors containing the true estimand is 95%. That is to say if I construct 95% confidence intervals for the sample mean again and again from the same data generating mechanism, 95% of the intervals I construct will contain the population mean.

Here, I wrote a function called ci_simulation that runs some simulations to show this is the case. From a standard normal distirbution, I sampled 25 observations and constructed a confidence interval. I did it 20 times and plotted the intervals using matplotlib.pyplot.errorbar. I save this plot under the name ci_simulation.png. The bar is colored red if the confidence interval does not caputre the true mean and blue if it does.

**Part 3:**
As you will see, there are two red intervels. It's good to think about these questions:
1) How many red intervals did you expect to see and why?
2) If there is a discrepency between the number of observed and expected red intervals, what explains this difference?

You can check out the answers to these questions in my code provided in "Confidence Intervals The Bootstrap.ipynb".

**Part 4:

