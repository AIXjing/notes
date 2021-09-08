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

* \\(\text{se_diff} = \sqrt{SE_1^2 + SE_2^2} = \sqrt{\frac{S_1^2}{n_1} + \frac{S_2^2}{n_2}}\\)

* \\(df = min(n_1 - 1, n_2 - 1)\\) which is a very conservative way *or using Welch's approximation*

#### 1.4.2 Pooled approach (\\(\sigma_1 = \sigma_2\\))

* \\(\text{Best estimate} = \bar{x}_1 - \bar{x}_2\\)

* \\(\text{se_diff} = \sqrt{SE_1^2 + SE_2^2} = \sqrt{\frac{(n_1-1)*S_1^2 + (n_2-1)*S_2^2}{n_1+n_2 - 2}}\\)

* \\(df = n_1 + n_2 - 2\\) 
