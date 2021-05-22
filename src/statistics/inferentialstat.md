# Inferential Statistics

[Here is the course link!](https://www.coursera.org/learn/inferential-statistics-intro/home/welcome)


## 1 CLT and Sampling

### 1.1 Sampling Variability and CLT


Sample distribution

Sampling distribution

population mean (\\(\mu \\)) and population standard deviation (\\(\sigma \\))

\\[
    \mu = \frac{x_1 + x_2 + ... + x_N}{N}
 \\]

 \\[
    \sigma = \sqrt{\frac{\sum\limits_{i=1}^{N}(x_i - \bar{x})^2}{N}}
 \\]

 For sampling distribution, 

 * **mean**(\\(\bar{x}) \approx \mu \\) 

 * **standard error:**  SD(\\(\bar{x}) \\)) < \\(\sigma \\)

 [The link to check up the shape of population distribution](https://gallery.shinyapps.io/CLT_mean/)


**Central Limit Theorem (CLT):** The distribution of sample statistics is nearly normal, centered at the population mean, and with a standard deviation equal to the population standard deviation divided by square root of the sample size.

\\[
    \bar{x} \sim N(mean = \mu, SE = \frac{\sigma}{\sqrt{n}}) 
\\]

N refers to the shape of distribution, meaning normal distribution.

\\(\sigma\\) is usually unknown, so s is used to replace \\(\sigma\\)


* **standard deviation (\\(\sigma\\)) vs. standard error (SE)**

    - \\(\sigma\\) measures the variability in the data

    - SE measures the variability in the sample mean (point estimates)


* sample size increases -> SE decreases *(either from conceptual or mathematically \\(SE = \frac{\sigma}{\sqrt{n}}\\) point of view)*

* To reduce skewness, either increase sample size (observations) or number of samples

* **Sampling distribution will be nearly normal only (the condition of CLT)if**

    - the sample size is sufficiently large (n ≥ 30 or larger if the data are considerably skewed) or the population is known to have a normal distribution

    - the observations in the sample are independent: random sample/assignment and n < 10% of population if sampling without replacement

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