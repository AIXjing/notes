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

 * mean(\\(\bar{x}) \approx \mu \\) 

 * **standard error:**  SD(\\(\bar{x}) \\)) < \\(\sigma \\)

 [The link to check up the shape of population distribution](https://gallery.shinyapps.io/CLT_mean/)


**Central Limit Theorem (CLT):** The distribution of sample statistics is nearly normal, centered at the population mean, and with a standard deviation equal to the population standard deviation divided by square root of the sample size.

\\[
    \bar{x} \sim N(mean = \mu, SE = \frac{\sigma}{\sqrt{n}}) 
\\]

N refers to the shape of distribution, meaning normal distribution.

\\(\sigma\\) is usually unknown, so s is used to replace \\(\sigma\\)

sample size increases -> SE decreases

To reduce skewness, either increase sample size (observations) or number of samples