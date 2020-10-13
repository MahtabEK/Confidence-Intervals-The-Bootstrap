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

**Part 4:**

Here, I wrote a function called num_propper_length which takes as its only argument an integer n. num_propper_length simulates 1000 datasets of length n, compute confidence intervals for those datasets, compute the lengths of those intervals, and then returns the number of intervals which are no longer than 0.1 units.

**Part 5:**

Here is a question. If you run the code, you will see that 891 (or approximately 89%) of the intervals are longer than 0.1.
Why do you think this is the case?

You can check out the answers to these questions in my code provided in "Confidence Intervals The Bootstrap.ipynb".



**Section 2**

**Part 1:**

The dataset hockey_stats.csv contains information about hockey draftees. I use this data to investigate the relationship between height and age on weight.

First, I load in the hockey_draftees_train.csv data into pandas. then, I fit a linear model of weight (wt) explained by height (ht) and age(age). I call my fitted model, model.

**Part 2:**

Then, I print out the R-squared for this model.

**Part 3:**

Now, we want to see how well this model performs out of sample. For this reason, I load in the hockey_draftees_test.csv file into a dataframe. Then, I use my model to make predictions, and print the r-squared on the out of sample (oos) data.

**Part 4:**

A point estimate of the rsquared is nice, but what I really want is uncertainty estimates. For that, I need a confidence interval. To estimate how uncertain I am in the out of sample r-squared, let's use the bootstrap.

I wrote a function called bootstrap which takes three arguments:

- data, which is a dataframe, and
- model which is an statsmodel ols model. data should look the the data model was trained on so that we can use model to make predictions on data.
- numboot which is an integer denoting how many bootstrap replications to perform.

I wrote bootstrap to perform bootstrap resampling for the out of sample r-squared. I used pd.DataFrame.sample with replace = True to perform the resampling.

Bootstrap returns a numpy array of bootstraped rsquared values.

**Part 5:**

Here, I use my bootstrap function to plot 10,000 bootstrap replicates as a histogram.

**Part 6:**

I use the bootstrap replicates to estimates to obtain a bootstrapped 95% confidence interval. I called the upper confidence bound ci_upper and the lower confidence bound ci_lower.
