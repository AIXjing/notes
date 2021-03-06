# Inferential Statistics

[Here is the course link!](https://www.coursera.org/learn/inferential-statistics-intro/home/welcome)

[Summary of leaning objectives for each section](https://www.notion.so/Inferential-Statistics-5dd1ac55e304409898a5877aadff7ecc)

## 1 CLT and Sampling

### 1.1 Sampling Variability and CLT

#### 1.1.1 Sample distribution and sampling distribution

- Sample distribution: sample mean and sample variability (standard deviation)

- Sampling distribution

    population mean (\\(\mu \\)) and population standard deviation (\\(\sigma\\))

    \\[
        \mu = \frac{x_1 + x_2 + ... + x_N}{N}
    \\]

    \\[
        \sigma = \sqrt{\frac{\sum\limits_{i=1}^{N}(x_i - \bar{x})^2}{N}}
    \\]

    *Most of time, population standard deviation \\(\sigma\\) is not known. Thus, \\(\sigma\\) is usually replaced by sampling standard deviation s*

    * **mean**(\\(\bar{x}) \approx \mu \\) 

    * **standard error:**  \\(SE = \frac{\sigma}{\sqrt{n}}\\) < \\(\sigma\\)

 [The link to check up the shape of population distribution](https://gallery.shinyapps.io/CLT_mean/)

#### 1.1.2 Central Limit Theorem (CLT)

**The distribution of sample statistics is nearly normal, centered at the population mean, and with a standard error equal to the population standard deviation divided by square root of the sample size.**

\\[
    \bar{x} \sim N(mean = \mu, SE = \frac{\sigma}{\sqrt{n}}) 
\\]

*\\(N\\) refers to the shape of distribution, meaning normal distribution.*

*\\(\sigma\\) is usually unknown, so s is used to replace \\(s\\) - sampling standard deviation*


#### 1.1.3 Other important concepts and rules

* **standard deviation (\\(\sigma\\)) vs. standard error (SE)**

    - \\(\sigma\\) measures the variability in the data

    - SE measures the variability in the sample mean (point estimates)


* sample size increases -> SE decreases *(either from conceptual or mathematically \\(SE = \frac{\sigma}{\sqrt{n}}\\) point of view)*

* To reduce skewness, either increase sample size (observations) or number of samples

* **Sampling distribution will be nearly normal only if (the condition of CLT)**

    - the sample size is sufficiently large (n ≥ 30 or even larger if the data are considerably skewed) or the population is known to have a normal distribution

    - the observations in the sample are independent: random sample/assignment and n < 10% of population if sampling without replacement

</br>

### 1.2 Confidential Intervals

#### 1.2.1 Confidential Intervals

**confidence interval** is defined as the plausible range of values for a population parameter. 

**confidence level** is defined as the percentage of random samples which  yield confidence intervals that capture the true population parameter.

**confidence interval for a population mean:**

\\[
    \bar{x} \pm z\frac{s}{\sqrt{n}}        
\\] 
    
**margin of error** (ME) = \\(z\frac{s}{\sqrt{n}} \\)

- for 95% CI: \\(\bar{x} \pm 2SE\\) i.e., \\(ME = 2SE\\)

*conditions for this confidence interval is the same as conditions for CLT (independent and sample size)*

![image](https://user-images.githubusercontent.com/41487483/119108985-0fff2a80-ba21-11eb-85e6-edf4997e6839.png)

[z-table](http://www.z-table.com/)

#### 1.2.2 z-score (not covered in the course)

* [z-score for a single value](https://www.usablestats.com/lessons/zarea) 

    Given we know the population parameters (\\(\mu\\) and \\(\sigma\\)), calculate z-score for any individual in the population:

    \\[
        z = \frac{(x - \mu)}{\sigma}    
    \\]

    Using z-table, the probability can be calculated.

* [z-score for a sample mean](https://www.usablestats.com/lessons/1samplez)

    \\[
        z = \frac{(\bar{x} - \mu)}{\frac{\sigma}{\sqrt{n}}}    
    \\]

* **Empirical rule**

    - 68% of values fall within 1 SE of the mean
    
    - 95% fall within 2 SE of the mean

    - 99% fall within 3 SE of the mean


#### 1.2.3 Accuracy vs. Precision

* **Accuracy**: whether or not the CI contains the true population paramter.

* **Precision**: the width of a confidence intervals.

Increasing CL, accuracy increases but precision decreases.

* To get a higher precision and high accuracy - increase sample size


### 1.2.3 Required sample size for ME

\\[
    ME = z \frac{s}{\sqrt{n}}    \rightarrow n = \Bigg(\frac{z s}{ME}\Bigg)^2
\\]


## 1.3 R vs. sampling distribution

1. Load the package and dataset(ames)

```r
    library(statsr)
    library(dplyr)
    library(shiny)
    library(ggplot2)

    data(ames)
```

2. Distribution of areas of homes and summary statistics

```r
ames %>%
    summarise(mu = mean(area), pop_med = median(area), 
        sigma = sd(area), pop_iqr = IQR(area),
        pop_min = min(area), pop_max = max(area),
        pop_q1 = quantile(area, 0.25),  # first quartile, 25th percentile
        pop_q3 = quantile(area, 0.75))  # third quartile, 75th percenti
```

3. Sample randome 50 houses and calculate the average area

```r
samp1 <- ames %>%
    sample_n(size=50)

samp1 %>%
    summarise(x_bar = mean(area))

# or combine above two code chunks into one
samp1 <- ames %>%
    sample_n(size=50) %>%
        summarise(x_bar = mean(area))
```

4. Estimate population mean by using sampling distribution

Take 15,000 samples of size 50 from the population (`rep_sample_n`), calculate the mean of each sample, and store each result in a vector called 'sample_means50'.

```r
sample_means50 <- ames %>%
  rep_sample_n(size = 50, reps = 15000, replace = TRUE) %>%
    summarise(x_bar = mean(area))

ggplot(data = sample_means50, aes(x = x_bar)) +
  geom_histogram(binwidth = 20)
```

To get the summary statistics of 15,000 sample means, analyze the statistics from the 'sample_means50', which is actually a dataset containing 15,000 observations(x_bar).

```r
sample_means50 %>%
    summarise(sampling_x_bar = mean(x_bar))
```

## 1.4 Python vs. sampling distribution

1. Load packages and import dataset

```py
import pandas as pd
import numpy as np
import random as random
import math
import matplotlib.pyplot as plt

ames = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/ames.csv")
#ames.head
#ames.columns
```

2. Distribution of population

```py
mu = np.average(ames["Lot.Area"])
sigma = np.std(ames["Lot.Area"])

plt.hist(ames["Lot.Area"],30, range=[0, mu+5*sigma])
plt.show()
#right skewed distribution
```

3. Randomly take 10 samples

```py
samp1 = ames.sample(n=10,replace=True)
```

4. Take 1000 samples with size 200

```py
size = 200
num_samp = 1000
samp_mean = []

for m in range(num_samp):
  samp = ames.sample(n=size,replace=True)
  x_bar_samp = np.average(samp["Lot.Area"])
  samp_mean.append(x_bar_samp)
  m += 1

x_bar_samp_mean = np.average(samp_mean)
x_bar_samp_se = np.std(samp_mean)/(math.sqrt(size))

print(x_bar_samp_mean)
print(x_bar_samp_se)

plt.hist(samp_mean, 20, range=[5000,15000])
plt.show()
```

</br>

## 2 Hypothesis testing and significance

### 2.1 Hypothesis testing (for a mean)

- Null hypothesis - \\(H_0\\) 

- Alternative hypothesis - \\(H_A\\)

![image](https://user-images.githubusercontent.com/41487483/119312937-3e744400-bc73-11eb-9396-704d391112eb.png)

*The hypothesis is always about pop.parameters, never about sample statistics (because the sample statistics is certain).*

* **p-value** - P(observed or more extreme outcome | \\(H_0\\) true)

    Given \\(n = 50, \bar{x} = 3.2, s = 1.74, SE = 0.246\\) 
    
    We are looking for \\(P(\bar{x} > 3.2 | H_0 : \mu = 3) \\)

    Since we believe that null hypothesis is true, \\(\bar{x} \sim N(\mu = 3, SE = 0.246)\\) based on the CLT.

    *test statistics*: z-score = (3.2-3)/0.246 = 0.81, which is used to calculate the p-value (the probability of observing data at least favorable to the alternative hypothesis as our current data set, if the null hypothesis was true)
    
    p-value = P(z > 0.81) = 0.209

**Decision based on the p-value**

- p-value < the **significant level**, \\(\alpha\\) (usually 5%): it is unlikely to observe the data if the null hypothesis is true. - Reject \\(H_0\\)

- p-value ≥ \\(\alpha\\): it is likely to occur even if the null hypothesis were true. - Do no reject \\(H_0\\)


**two-sided(tailed) tests**

In the same case, \\(P(\bar{x} > 3.2 \text{  or  } \bar{x} > 2.8| H_0 : \mu = 3) \\)

p-value = P(z > 0.81) + P(z < -0.81) = 0.418 - fail to reject \\(H_0\\).

![image](https://user-images.githubusercontent.com/41487483/119316226-ff47f200-bc76-11eb-944a-1c63ee237ebd.png)


### 2.2 Significance

#### 2.2.1 Inference for other estimators

* point estimates: 

    *\\(\hat{\theta}\\): \\(\hat{\theta}_{LMS}\\) or (\\(\hat{\theta} _{MAP}\\)) the concept might be different from MIT statistics course*

    1. sample mean

    2. difference between sample means

    3. sample proportion \\(\hat{p}\\)

    4. difference between two proportions

* two requirements:  

    - nearly normal sampling distribution

    - unbiased estimator assumption: **point estimates** are unbiased, i.e., the sampling distribution of the estimate is centered at the true population parameter it estimates.

#### 2.2 Decision errors

![image](https://user-images.githubusercontent.com/41487483/125154284-93074c00-e159-11eb-940d-bbec5059b97d.png)

**Decrease significance level (\\(\alpha\\)) decrease Type I error rate**

\\(P(\text{Type I error}|H_0 \text{ true}) = \alpha\\)

* **Choosing \\(\alpha\\)**

    - if Type I error is dangerous or costly, choose a small significance level (e.g. 0.01)

    - if Type II error is dangerous or costly, choose a high significance level (e.g. 0.10)

![image](https://user-images.githubusercontent.com/41487483/125154728-c054f980-e15b-11eb-962c-f200d24dedd0.png)

\\(\beta\\) depends on the **effect size \\(\delta\\)** - difference between point estimate and null value.
    
#### 2.2.3 Significance level vs. confidence level

* complement each other depending on one-sided or two -sided tests

    - two-sided tests: Significance level = confidence level 
        
        CL = 1 - alpha
    
    ![image](https://user-images.githubusercontent.com/41487483/125154861-791b3880-e15c-11eb-98d8-55756cf27eaa.png)

    - one-sided tests: Significance level ≠ confidence level

        CL = 1 - 2 x alpha

        ![image](https://user-images.githubusercontent.com/41487483/125154873-8cc69f00-e15c-11eb-9701-9d1498add575.png)

#### 2.2.4 Statistical vs. practical significance

* practical significance 

    Real difference between point estimator and null value are easier to detect with larger samples (effect size)

* statistical significance 

    very large samples will result in statistical significance even for tiny differences between sample mean and the null value (effect size), even when the difference is not practically significant. 


