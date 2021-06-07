# Probability - The Science of Uncertainty and Data (2021)

Use the course to re-build my statistics knowledge.

[The course link](https://www.edx.org/course/probability-the-science-of-uncertainty-and-data)

[The Book](https://ece307.cankaya.edu.tr/uploads/files/introduction%20to%20probability%20(bertsekas,%202nd,%202008).pdf)

## 1 Sample Space and Probability


### 1.1 Sample space - A set of outcomes

* discrete/finite example

* continuous example

       
### 1.2 Probability Axioms

* Nonnegativity
\\(P(A) \geq 0 \\)

* Normalization
  \\( P( \Omega ) = 1 \\), \\(\Omega \\) is the entire sample space.

* (finite) Additivity: A and B are disjoint, then the probability of their unions satisfies \\(P(A \cup B) = P(A) + P(B)\\) (to be strengthened later)


#### 1.2.1 Simple consequences of the axioms

1. For a sampe space consist of a finite number of disjointed events,
\\[ 
    P({s_1, s_2, ...., s_n}) = P(s_1) + P(s_2) + ...... P(s_n)
\\]

2. \\(A \subset B\\), then \\(P(A) \leq P(B)\\)

3. \\(P(A \cup B) = P(A) + P(B) - P(A \cap B)\\)

4. \\(P(A \cup B) \leq P(A) + P(B))\\)

### 1.3 Probability calculations

#### 1.3.1 Uniform Probability Law

* Discrete example

    If the sample space consists of n possible outcomes which are equally likely (i.e., all single-element events have the same probability),
    \\[ 
        P(A) = \frac{\text{number of elements of A}}{n}
    \\]

* continuous example

    probability = area


#### 1.3.2 Discrete but infinite sample space

* Sample space: {1, 2, 3 ....}

    Given \\(P(n) = \frac{1}{2^n}\\), n = 1, 2, 3....

    As \\( P(\Omega) = 1 \\): \\(\frac{1}{2} + \frac{1}{4} + ....=  \sum\limits_{n=1}^\infty \frac{1}{2^n} = \frac{1}{2}\sum\limits_{n=0}^\infty \frac{1}{2^n} = \frac{1}{2}\frac{1}{1-1/2} = 1\\) 


#### 1.3.3 Countable aditivity axiom

*Additivity holds only for "**countable**" sequences of events*

If \\(A_1, A_2, A_3 ...\\) is an \\(\underline{\text{infinite sequence of disjoined events}}\\),

\\[
    P(A_1 \cup A_2 ......) = P(A_1) + P(A_2) + ......
\\]

<br>

### 1.4 Mathematical background

#### 1.4.1 Sets - A collection of distinc elements 

* finite: e.g. {a, b, c, d}

* infinite: the reals (R)

* \\( \Omega \\) - the universal set

* Ø - empty set

*What are reals?*

*The reals include rational numbers (terminating decimals and non-terminating recurring decimals and irrational numbers (non-terminating non-reccuring decimals*

#### 1.4.2 Unions and intersection

#### 1.4.3 De Morgans' Law

* \\( (S \cap T)^c = S^c \cup T^c \\) and \\( (S \cup T)^c = S^c \cap T^c \\)

* \\( (S^c \cap T^c)^c = S \cup T \\)

#### 1.4.4 Other important mathematical backgrounds

* Sequences and their limits 
    
    *squence: an enumerated collection of objects*

* When does a sequence converge

    * if \\(a_i \leq a_{i+1}\\)

        - the sequence "converge to \\(\infty\\)"

        - the sequence converge to some real number a 
    
    * if \\(|a_i - a| \leq b\\), for \\(b_i \to 0\\), then \\(a_i \to a\\)

* Infinite series

    *series(infinte sums) vs. summation(finite sums)*

    \\(\sum\limits_{n=1}^\infty a_i = \lim\limits_{n\to\infty}\sum\limits_{i=1}^n a_i\\) 

    - \\(a_i \leq 0\\): limit exists

    - if term \\(a_i\\) do not all have the same sign:

        a. limit does not exist

        b. limit may exist but be different if we sum in a different order

        c. **Fact**: limit exists and independent of order of summation if  \\(\sum\limits_{n=1}^\infty |a_i| \leq \infty\\) 

* Geometric series (等比数列、等比级数)

    \\(\sum\limits_{i=0}^\infty a^i = 1 + a + a^2 + ...... = \frac{1}{1-a} \text{           |a| < 1} \\)


### 1.4 Sets

#### 1.4.1 Countable and uncountable infinite sets

* Countable

    * integers, pairs of positive integers, etc.

    * rational numbers q (有理数), with 0 < q < 1

* Uncountable - *continuous numbers*

    * the interval [0, 1]

    * the reals, the plane, etc.

    *How to prove the reals are uncountable - "Control's diagonalization argument"*

<br>


## Unit 2 Conditioning and independence

Refer to Section 1.3 - 1.5 in the textbook

### 2.1 Conditional and Bayes' Rules

#### 2.1.1 The definition of conditional probability

P(A|B) = "probability of A, given that B occurred"

\\[
    P(A|B) = \frac{P(A \cap B )}{P(B)}
\\]

defined only when P(B) > 0

#### 2.1.2 Conditional probabilities share properties of ordinary probabilities

* \\(P(A|B) \geq 0\\)

* \\(P(\Omega|B) = 1\\)

* \\(P(B|B) < 0\\)

* If \\(A \cap C = Ø\\), then \\(P(A \cup C|B) = P(A|B) + P(C|B)\\) also only applies to countable and finite sequence (countable additivity axioms).


#### 2.1.3 Models base on conditional probabilities

![image](https://user-images.githubusercontent.com/41487483/117574884-993c6600-b0df-11eb-9125-c5501b77d001.png)


**1. The multiplication rule**

    \\(P(A \cap B) = P(B)P(A|B) = P(A)P(B|A)\\)

    \\(P(A^c \cap B \cap C^c) = P(A^c \cap B) P(C^c|A^c \cap B) = P(A^c) P(B|A^c) P(C^c|A^c \cap B)\\)

    \\(P(A_1 \cap A_2...\cap A_n) = P(A_1) \prod\limits_{i=2}^n P(A_i|A_1 \cap A_2...\cap A_i)\\)

![image](https://user-images.githubusercontent.com/41487483/118396328-55051480-b64f-11eb-9c9e-9703528df69e.png)


**2. Total probability theorem**

![image](https://user-images.githubusercontent.com/41487483/118396377-9e556400-b64f-11eb-8e1a-f5530bb63fd3.png)

**3. Bayes' rules**

![image](https://user-images.githubusercontent.com/41487483/118396464-eeccc180-b64f-11eb-9080-e7e86ad223bf.png)


### 2.2 Independence

#### 2.2.1 Conditional independence

Independent of two events

* Intuitive "definition": P(B|A) = P(B) 

    - Occurence of A provides no new information about B

Definition of independence:

\\(P(A \cap B) = P(A) \times P(B)\\)

*whether two events disjoined or joined is not associated with independence*

**Independent of events complements**

If A and B are independent, then A and \\(B^c\\) are independent. 

**Independent of events complements**

![image](https://user-images.githubusercontent.com/41487483/118397139-df9b4300-b652-11eb-9e1c-e8b293e070fc.png)

**Conditioning may affect independence**

![image](https://user-images.githubusercontent.com/41487483/118397436-35241f80-b654-11eb-89cf-d6eacefd924e.png)


#### 2.2.2 Independence of a collection of events 

* Intuitive "definition": Information on some of the events does not change probabilities related to the remaining events

* Definition: Events \\(A_1, A_2,....., A_n\\) are called independent if: 

    \\(P(A_i \cap A_j \cap .... \cap A_m) = P(A_i)P(A_j)...P(A_m)\\)


**Pairwise independence**

n = 3:

\\(P(A_1 \cap A_2) = P(A_1)P(A_2)\\)

\\(P(A_1 \cap A_3) = P(A_1)P(A_3)\\)

\\(P(A_2 \cap A_3) = P(A_2)P(A_3)\\)

vs. 3-way indenpendence

\\(P(A_1 \cap A_2 \cap A_3) = P(A_1)P(A_2)P(A_3)\\)

**Independence vs. pairwise independence**

![image](https://user-images.githubusercontent.com/41487483/118398068-4d496e00-b657-11eb-91d3-ade5aa82f245.png)


#### 2.2.3 Reliability
![image](https://user-images.githubusercontent.com/41487483/118398123-7bc74900-b657-11eb-8f00-9313ffc249f6.png)


## Unit 3 Couting

### 3.1 Basic counting principle

r stages and \\(n_i\\) choices at stage i give the total number of possible choices \\( n_1 * n_2 * ....n_r \\)

### 3.2 Permutation

* **Permutation** - number of ways of ordering n elements (repetition is prohibited)

\\[n * (n-1) * (n-2) * ... * 2 * 1 = n!\\]

* Number of subsets of {1, 2, ...n} = \\(2^n\\)

### 3.3 Combinations 

* **combinations** \\(\binom{n}{k}\\)- number of *k*-element subsets of a given *n*-element set

    *How is combination equation derived?*

    Two ways of constructing an **ordered** sequence of *k* **distinct** items:

    - choose the *k* items one at a time: 

        \\[
            n (n-1) ... (n-k+1) = \frac{n!}{k!(n-k)!}
        \\]

    - choose *k* items, then order them:

        \\[
            \left(
            \begin{array}{c}
            n \\\\
            k
            \end{array}
            \right)k!
        \\]

    There we have 
        \\[
            \left(
            \begin{array}{c}
            n \\\\
            k
            \end{array}
            \right) = \frac{n!}{k!(n-k)!}
        \\]
    

### 3.3 Binominal coeffficient 

* **Binominal coeffficient** \\(\binom{n}{k}\\) - Binomial probabilities

    Toss coins n times and each toss is given independent, P(Head) = p

    \\[
        P(\text{k heads}) = \binom{n}{k}p^k (1-p)^{n-k}
    \\]

    If asking P(k heads without ordered), then 

     \\[
        P(\text{k heads}) = p^k (1-p)^{n-k}
    \\]

    Therefore, \\(\binom{n}{k}\\) is the number of *k*-head sequence


### 3.4 Partitions

![image](https://user-images.githubusercontent.com/41487483/119098744-73d02600-ba16-11eb-8406-20acdf555e25.png)

* **multinomial coeffecient** (number of partitions) =

    \\[
        \frac{n!}{n_1! n_2! ... n_r!}
    \\]

If r = 2, then \\(n_1 = k\\) and \\(n_2 = n - k\\). There is \\(\frac{n!}{n! (n-k)!}\\) which is \\(\binom{n}{k}\\)

* A simple example

![image](https://user-images.githubusercontent.com/41487483/119102618-83516e00-ba1a-11eb-86e6-b87e6ecf3467.png)

![image](https://user-images.githubusercontent.com/41487483/119102964-e8a55f00-ba1a-11eb-9693-d29eb512ac3f.png)

## 4 Discrete random variables

### 4.1 Probability mass function (PMF)

**Random variable**(r.v.): a function from the sample space to the real numbers, notated as X.

**PMF**: probability distribution of X 

\\[
    p_X(x) = P(X = x) = P({w \in \Omega, s.t. X(\omega) = x})
\\]

### 4.2 Discrete Random variable examples

#### 4.2.1 Bernoulli random variables 

with parameter \\(p \in [0,1]\\)

\\[
    p_X(x) = \begin{cases} 1, p(x) = p \\\ 0, p(x) = 1 - p \end{cases} 
\\]

- Models a trial that results in either success/failure, Heads/Tails, etc.

- **Indicator random variables** of an event A, \\(I_A\\) iff A occurs

#### 4.2.2 Uniform random variables 

with paramters a,b

- Experiment: pick one of a, a+1 .... b at a random; all equally likely

- Sample space; {a, a + 1, .... b}

- Random variables X: \\(X(\omega) = \omega\\)


#### 4.2.3 Binomial random variables 

with parameters: pasitive integer \\(n; p \in [0,1]\\)

- Experiment: n independent toses of a coin with P(Heads) = p

- Sample space: set of sequences of H and T of length n

- Random variables X: number of Heads observed

- Model of: number of successes in a given number of independent trials 

\\[
    p_X(k) = \left(\begin{array}{c} n \\\\ k \end{array}  \right)p^k(1-p)^{n-k}, k = 0, 1 ..., n
\\]

#### 4.2.4 Geometric random variables 

with parameter p: 0 < p ≤ 1

- Experiment: infinitely many independent tosses of a coin: P(Heads) = p

- Random variable X: number of tosses until the first Heads

- Model of waiting times; number of tirals until a success

\\[
    p_X(k) = P(X = k) = P(T...TH) =(1-p)^{k-1}p, k = 1,2,3...    
\\]

### 4.3 Expectation/mean of a random variable

- **Definition**: 

    \\[
        E[X] = \sum\limits_{x} xp_X(x)
    \\]

- Interpretation: average in large number of independet repetitions of the experiment

- Elementary properties

    * If X ≥ 0, then E(X) ≥ 0

    * If a ≤ X ≤ b, then a ≤ E[X] ≤ b

    * If c is a constant, E[c] = c

    * The expected value rule: 

        \\[
            E[Y] = \sum\limits_y yp_Y(y) = E[g(X)] = \sum\limits_x g(x)p_X(x)    
        \\]

    * Linearity of expectation: \\(E[aX+b] = aE[X] + b\\)

### 4.4 Variance - a measure of the spread of a PMF

#### 4.4.1 Definition of variance: 

\\[
    var(X) = E[(X - \mu)^2] = \sum\limits_x (x - \mu)^2 p_X(x)
\\]

standard deviation: \\(\sigma_X = \sqrt{var(X)}\\)

#### 4.4.2 Properties of the variance 

- Notation: \\(\mu = E[X] \\)

- \\(var(aX + b) = a^2var(X)\\)

- A useful formula:

    \\[
        var(X) = E(X^2) - (E[X])^2    
    \\]

**Summary of Expectation and Variance of Discrete Random Variables**

| Random Variables | Formula       | E(X)  |  var(X) |
| -----------------|:-------------:| -----:|--------:|
|      Bernoulli (p)  | \\(p_X(x) = \begin{cases} 1, p(x) = p \\\ 0, p(x) = 1 - p \end{cases} \\) | \\(p\\)|\\(p(1-p)\\)|
|      Uniform (a,b)   | \\(p_X(x) = \frac{1}{b-a}, a ≤ x ≤ b\\) | \\(\frac{a+b}{2}\\)|\\(\frac{1}{12}(b-a)(b-a-2)\\)|
|Binomial \\(p \in [0,1]\\) | \\(p_X(k) = \left(\begin{array}{c} n \\\\ k \end{array}  \right)p^k(1-p)^{n-k}, k = 0, 1 ..., n\\) | \\( np \\)| \\(np(1-p)\\)|
| Geometric  \\(0 < p ≤ 1\\)  | \\(p_X(k) = (1-p)^{k-1}p, k = 1,2,3.... \\) | \\(\frac{1}{p}\\)|\\(\\)|

### 4.5 Conditional PMF and expectation, given an event

#### 4.5.1 Conditional PMFs

\\(p_{X|A}(x|A) = P(X = x|A)\\), given A = {Y = y}

\\[
    p_{X|Y}(x|y) = \frac{p_{X,Y}(x,y)}{p_Y(y)}    
\\]

#### 4.5.2 Conditional PMFs involing more than two random variables

- \\(p_{X|Y,Z}(x|y,z) = P(X = x|Y = y, Z = z) = \frac{P(X=x,Y=y,Z=z)}{P(Y=y, Z=z)} = \frac{P_{X,Y,Z}(x,y,z)}{P_{Y,Z}(y,z)} \\)

- Multiplication rules: \\(p_{X,Y,Z}(x,y,z) = p_X(x)p_{Y|X}(y|x)p_{Z|X,Y}(z|x,y) \\)

- Total probability and expectation theorems

    \\(p_X(x) = P(A_1)p_{X|A_1}(x) + ... + P(A_n)p_{X|A_n}(x) \implies p_X(x) = \sum\limits_y p_Y(y)p_{X|Y}(x|y)\\)

    \\(E[X] = P(A_1)E[X|A_1] + ... + P(A_n)E[X|A_n] \implies E[X] = \sum\limits_y p_Y(y) E[X|Y = y]\\)

### 4.6 Multiple random variables and joint PMFs

#### 4.6.1 Joint PMF

\\[
    p_{X,Y}(x,y) = P(X = x, Y =y)
\\]

- \\(\sum\limits_x \sum\limits_y p_{X,Y}(x,y) = 1\\)

- Marginal PMFs: \\(p_X(x) = \sum\limits_y p_{X,Y}(x,y)\\)

    \\(p_Y(y) = \sum\limits_x p_{X,Y}(x,y)\\)

#### 4.6.2 Functions of multiple random variables

\\(Z = g(X,Y)\\)

- PMF: \\(p_Z(z) = P(Z=z) =P(g(X,Y) = z) \\)

- Expected value rules: \\(E[g(X,Y)] = \sum\limits_x \sum\limits_y g(x,y) p_{X,Y}(x,y)\\)

- Linearity of expectations

    * \\(E[aX + b] = aE[X] + b\\)

    * \\(E[X + Y] = E[X] + E[Y]\\)


#### 4.6.3 Independence of multiple random variables

- \\(P(X = x and Y = y) = P(X = x) \times P(Y = y), for all x, y \\)

- \\(P_{X|Y}(x|y) = P_X(x)\\) and \\(P_{Y|X}(y|x) = P_Y(y)\\)

- **Independence and expectations**

    * In general, \\(E[g(X,Y)] \neq g(E[X], E[Y])\\)

    * If X, Y are independent: \\(E[XY] = E[X]E[Y]\\)

        g(X) and h(Y) are also independent: \\(E[g(X)h(Y)] = E[g(X)]E[h(Y)]\\)

- **Independence and variances**

    * Always true: \\(var(aX) = a^2var(X)\\) and \\(var(X+a) = var(X)\\)

    * In general: \\(var(X+Y) \neq var(X) + var(Y)\\)

    * If X, Y are independent, \\(var(X,Y) = var(X) + var(Y)\\)

## 5 Continuous random variables

### 5.1 Probability density function (PDFs)

#### 5.1.1 Definition

![image](https://user-images.githubusercontent.com/41487483/120918805-91f48200-c6b6-11eb-9319-23713295480c.png)

*PDFs are not probabilities. Their units are probability per unit length.*

**Contiunous random variables**: a random variable is continuous **if it can be described by a PDF**.

- \\(P(X = a) = 0\\)

- \\(f_X(x) \geq 0\\)

- \\(\int\_{-\infty}^{+\infty}f(x)dx = 1\\)

**Expectation/Mean**

Expection/mean of a continuous random variable: *average in large number of independent repetitions of the experiment*

\\[
    E[X] = \int\_{-\infty}^{+\infty}xf_X(x)dx
\\]

**Properties of expectations**

- if X ≥ 0, then \\(E[X] ≥ 0\\)

- if a ≤ X ≤ b, then \\(a ≤ E[X] ≤ b\\)

- Expected value rule: \\(E[g(X)] = \sum\limits_{x} g(x) f_X(x) dx \\)

- Linearity: \\(E[aX + b] = aE(X) + b\\)


**Variance**

According to the definition of variance: \\(var(X) = E[(X - \mu)^2] \\)

\\[
    var(X) = \int\_{-\infty}^{+\infty} (x - \mu)^2 f_X(x) dx
\\] 

- Standard deviation = \\(\sigma_X = \sqrt{var(X)} \\)

- \\(var(aX + b) = a^2 var(X)\\)

- \\(var(X) = E[X^2] - (E[X])^2\\)


**Summary of Expectation and Variance of continuous random variables**

| Random Variables | Formula       | E(X)  |  var(X) |
| -----------------|:-------------:| -----:|--------:|
|      Uniform     | \\(f(x) = \frac{1}{b-a}, a ≤ x ≤ b\\) | \\(\frac{a+b}{2}\\)|\\(\frac{(b-a)^2}{12}\\)|
| Exponential \\( \lambda > 0 \\) | \\(f(x) = \begin{cases} \lambda e^{-\lambda x}, x ≥ 0 \\\ 0, x < 0 \end{cases}\\) | \\(\frac{1}{\lambda}\\)|\\(\frac{1}{\lambda^2}\\)|


#### 5.1.2 Cumulative distribution functions (CDF)

CDF defination: \\(F_X(x) = P(X ≤ x )\\)

- Non-decreasing

- \\(F_X(x)\\) tends to 1, as \\(x \to \infty\\)

- \\(F_X(x)\\) tends to 0, as \\(x \to - \infty\\)

#### 5.1.3 Normal(Gaussian) random variables

1. Standard normal(Gaussian) random variables

    Stardard  normal \\(N(0,1): f_X(x) = \frac{1}{\sqrt{2\pi}} e^{-x^2/2} \\)

    - E[X] = 0

    - var(X) = 1

2. General normal(Gaussian) random variables

    General  normal \\(N(\mu,\sigma^2): f_X(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-(x-\mu)^2/2\sigma^2}, \sigma > 0 \\)

    - E[X] = \\( \mu \\)

    - var(X) = \\( \sigma^2 \\):\\( \sigma^2 \to small\\), the shape of normal distribution becomes more narrow.

3. Linear functions of a normal random variable

    - Let \\(Y = aX + b, X \sim N(\mu, \sigma^2)\\)

        \\(E[Y] = a\mu + b\\)

        \\(Var(Y) = a^2 \sigma^2 \\)

    - Fact: \\(Y \sim N(a\mu + b, a^2 \sigma^2)\\)

    - Special case: a = 0. There is Y = b, \\(N(b, 0)\\)

#### 5.1.4 Calculation of normal probabilities

1. **Standard normal tables** 

    \\(\Phi(y) = F_Y(y) = P(Y \leq y)\\) which can be find in the table, where y ≥ 0.

2. Standardizing a random variable

    \\(X \sim N(\mu, \sigma^2), \sigma^2 > 0 \\)

    \\(Y = \frac{X - \mu}{\sigma}\\)