# Inferential Statistics with Python 

*Notes from the 2nd course in "Statistics with Python Specialization" on Coursera*

Commonly used Python library for inferential statistics

```py
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import statsmodels.api as sm
```

## 1 Confidence interval

[Example](https://colab.research.google.com/drive/18jGIoV-b3UWxA_BZwviKUrQnN1747yo-#scrollTo=2seqqn_-Th5a) using NHANES dataset.

### 1.1 One proportion (categorical variables)

\\[
    \text{confidence interval} = \text{best estimate} \pm \text{mutiplier}*\text{standard error} 
\\]


* \\(\text{standard error} = \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}\\)

* \\(\text{Best estimate} = \text{sample proportion}\\)

#### Method 1 using cross table output

1. Cross table

    One looking at two proportions from two groups, crosstable might be useful `pd.crosstable(dx[col1], dx[col2])`.

    *NB: the column names of the cross table are not a list, and thus needs to be renamed by `dx.columns = ['col1','col2']` in some cases*

2. Proportion calculation

    ```py
        dz = dx.groupby(['RIAGENDRx']).agg({'SMQ020x': [lambda x: np.mean(x=="yes"), np.size]})
        dz.columns = ['Proportion', 'Total_n']
    ```

    Then, calculate p, n, se, respectively

#### Method 2 using sm library

`sm.stats.proportion_confint(prop*n, n, alpha = 0.05)`

### 1.2 Two proportion from two independent variables

\\[
    \text{confidence interval} = \text{best estimate} \pm \text{mutiplier}*\text{se_diff}      
\\]

* \\(\text{SE}_1 = \sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1}}\\)

* \\(\text{SE}_2 = \sqrt{\frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}\\)

* \\(\text{se_diff} = \sqrt{SE_1^2 + SE_2^2} = \sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1} + \frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}\\)

* \\(\text{Best estimate} = p_1 - p_2\\)

Calculate lower confidence interval and upper confidence interval respectively. *No sm method so far.*


### 1.3 Confidence interval for one mean (quantative variable)

* \\(\text{Best estimate} = \bar{x}\\)

* \\(\text{Standard error} = \frac{s}{\sqrt{n}}\\) 

    - *s* is the sample standard deviation `np.std(data, ddof=1)`

    - population standard deviation `np.std(data, ddof=0)`

* multiplier depends on the significant level and distribution (z or t). If t distribution, the shape depends on the degree of freedom.

* z distribution: `sm.stats.DescrStatsW(bmi_female).zconfint_mean()`

### 1.4 Confidence interval for two means from two independent populations

#### 1.4.1 Unpooled approach (\\(\sigma_1 \neq \sigma_2\\))

* \\(\text{Best estimate} = \bar{x}_1 - \bar{x}_2\\)

* \\(\text{se_diff} = \sqrt{SE_1^2 + SE_2^2} = \sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}\\)

* \\(df = min(n_1 - 1, n_2 - 1)\\) which is a very conservative way *or using Welch's approximation*

#### 1.4.2 Pooled approach (\\(\sigma_1 = \sigma_2\\))

* \\(\text{Best estimate} = \bar{x}_1 - \bar{x}_2\\)

* \\(\text{se_diff} = \sqrt{SE_1^2 + SE_2^2} = \sqrt{\frac{(n_1-1)*s_1^2 + (n_2-1)*s_2^2}{n_1+n_2 - 2}}\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}\\)

* \\(df = n_1 + n_2 - 2\\) 


## 2 Hypothesis test

**General steps:**

* Set up a Hypothesis \\(H_0\\) and significant level \\(\alpha\\)

* Check conditions:

    - simple random sample?

    - nearly normal distribution or sample size large enough 

    - calculate test statistics (z-score or t)

    \\[
        z = \frac{\text{Best estimate} - \text{hypothesized estimate}}{standard error of estimate}    
    \\]

    - find p-value and compare to \\(\alpha\\) and make conclusion - reject \\(H_0\\) or fail to reject \\(H_0\\)

### 2.1 Test on a population proportion

* set null hypothesis

    - \\(H_0: p_0\\)

    - \\(H_A: \hat{p}\\)

* Check conditions: \\(np \geq 10, n(1-p) \geq 10\\)

* calculate test statistics and p value

    \\[
        z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}    
    \\]

    *se is based on null hypothesis*

    - traditional method for p value: `p_val = 2*dist.norm.cdf(-np.abs(test_stat))`
    
    - `sm.stats.proportions_ztest()`

    - `sm.stats.binom_test()`


### 2.2 Test on difference in population proportions

* set null hypothesis

    \\(H_0: p_1 - p_2 = 0\\)

    \\(H_A: p_1 - p_2 \neq 0\\)

*  Check conditions: \\(n_1p_1 \geq 10, n_1(1-p_1) \geq 10, n_2p_2 \geq 10, n_2(1-p_2) \geq 10\\)

* calculate test statistics

    \\[
        z = \frac{\hat{p}_1-\hat{p_2}_1 - 0}{\sqrt{\hat{p}(1-\hat{p})(\frac{1}{n_1}+\frac{1}{n_2})}}    
    \\]

    *se is based on combined the proportion* \\(p = \frac{(n_1p_1 + n_2p_2)}{(n_1+n_2)}\\)

    - traditional method for p value: `p_val = 2*dist.norm.cdf(-np.abs(test_stat))`

    - t test: `sm.stats.ttest_ind(population1,population2)`

    - z score: `sm.stats.ztest(population1,population2)`

* Alternative approaches

    1. Chi-square text: different hypothesis and two-side hypothesis

    2. Fisher's Exact test

        - allow one-side hypothesis

        - typically for small sample size


### 2.3 Test on one population mean

* set null hypothesis

    \\(H_0: \mu = ?\\)

    \\(H_A: \mu \neq ?, \mu > ?, \mu < ?\\) depending on the research questions

* Exam results, check assumptions, summarize data (boxplot, QQplot, Histogram)

* calculate test statistics

    \\[
        t = \frac{\bar{x} - \mu}{\frac{s}{\sqrt{n}}}    
    \\]

    * s: sample standard deviation `np.std(x, ddof=1)`

    * `sm.stats.ztest()`

* What if normality doesn't hold

    - non-parametric test: 

        e.g. Wilcoxon signed Rank test (use median to do test statistics)

### 2.4 Test on a difference on population means based on paired data

* set null hypothesis

    \\(H_0: \mu_d = 0\\)

    \\(H_A: \mu_d \neq 0\\) 

* Exam results, check assumptions, summarize data (boxplot, QQplot, Histogram)

* calculate test statistics

    \\[
        t = \frac{\bar{x}_d - 0}{\frac{s_d}{\sqrt{n}}}    
    \\]

    * `sm.stats.ztest()` or `sm.stats.ttest_ind()`

    * should be in line with the confidence interval inference: 

    \\[
        \bar{x}_d \pm t* \frac{s_d}{\sqrt{n}}
    \\]

* Normality doesn't hold? - Wilcoxon signed rank est

### 2.4 Test on a difference on population means based on independent data

* set null hypothesis

    \\(H_0: \mu_d = 0 \text{ or } \mu_1 = \mu_2\\)

    \\(H_A: \mu_d \neq 0 \text{ or } \mu_1 \neq \mu_2\\) 

* Exam results, check assumptions, summarize data (boxplot, QQplot, Histogram)

* calculate test statistics

    \\[
        t = \frac{(\bar{x}_1 - \bar{x}_2) - 0}{se}  
    \\]

    * pooled approach (\\(\sigma_1^2 \approx \sigma_2^2\\)) variance

        \\[
            se = \sqrt{\frac{(n_1-1)s_1^2 + (n_2-1)s_2^2}{n_1+n_2 - 2}}\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}    
        \\]

        \\(df = n_1 + n_2 - 2\\)

    * unpooled approach (\\(\sigma_1^2 \approx \sigma_2^2\\) is not needed)

        \\[
            se = \sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}
        \\]

        \\(df = min(n_1-1,n_2-1)\\)

    * `sm.stats.ztest()` or `sm.stats.ttest_ind()`

    * `sm.stats.CompareMeans(bmi_female, bmi_male).ztest_ind(usevar='pooled')`

        The argument `bmi_female` should be the output of `sm.stats.DescrStatsW(data)`

        
