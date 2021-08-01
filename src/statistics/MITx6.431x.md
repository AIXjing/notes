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

    - \\(E[X] = 0\\)

    - \\(var(X) = 1\\)

2. General normal(Gaussian) random variables

    General  normal \\(N(\mu,\sigma^2): f_X(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-(x-\mu)^2/2\sigma^2}, \sigma > 0 \\)

    - \\(E[X] = \mu \\)

    - \\( var(X) = \sigma^2 \\)
    
        \\( \sigma^2 \to small\\), the shape of normal distribution becomes more narrow.

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

### 5.2 Conditioning on an event: multiple continuous r.v.'s

\\[
    P( X \in B|A) =  \int_B f_{X|A}(x)dx
\\]

#### 5.2.1 Conditional PDf of X, given that \\(X \in A \\)

\\[
    f_{X|X \in A}(x) = \begin{cases} 0, if x \notin A \\\\ \frac{f_X(x)}{P(A)}, if x \in A \end{cases}
\\]

#### 5.2.2 Conditional expectation of X, given an event

![image](https://user-images.githubusercontent.com/41487483/121066009-b5f4b800-c7c9-11eb-9e82-cca4ded3a17f.png)

#### 5.2.3 Memorylessness of the exponential PDF

![image](https://user-images.githubusercontent.com/41487483/121071392-2a325a00-c7d0-11eb-8e77-c14ded14fe0c.png)

#### 5.2.4 Total probability and expectation theorems

- Probability theorem: 

\\[
    P(B) = P(A_1)P(B|A_1) + \dotsb + P(A_n)P(B|A_n)
\\]

- For the discrete random variable: 

\\[
    p_X(x) = P(A_1)p_{X|A_1}(x) + \dotsb + P(A_n)p_{X|A_n}(x)
\\]

- For CDF: 

\\[
    F_X(x) = P(X \leq x) = P(A_1)P(X \leq x | A_1) + \dotsb + P(A_n)P(X \leq x | A_n) 
    \\\\= P(A_1)F_{X|A_1}(x) + \dotsb + P(A_n)F_{X|A_n}(x)
\\]

- For PDF, the derivative of CDF:

\\[
    f_X(x) = P(X \leq x) = P(A_1)f_{X|A_1}(x) + \dotsb + P(A_n)f_{X|A_n}(x)
\\]

- Integral above equation, we will obtain the expectation equation:

\\[
    \int xf_X(x)dx = P(A_1) \int xf_{X|A_1}(x)dx + \dotsb + P(A_n) \int xf_{X|A_n}(x)dx
\\]

\\[
    E[X] = P(A_1)E[X|A_1] + \dotsb + P(A_n)E[X|A_n]    
\\]

### 5.3 Mixed random varibles

#### 5.3.1 Mixed distirbutions

\\[
     X = \begin{cases} Y, \text{with probability } p \text{ (Y discrete)}\\\\ Z, \text{with probability } 1-p \text{ (Z continuous)} \end{cases}   
\\]

* do not have PDF or PMF but can be defined with CDF and expectation

    \\[
        F_X(x) = p P(Y \leq x) + (1-p) P(Z \leq x)
        \\\\
        =pF_Y(x) + (1-p)F_Z(x)
        \\\\
        = E[X] = p E[Y] + (1-p) E[Z]
    \\]

    ![image](https://user-images.githubusercontent.com/41487483/121077061-6fa65580-c7d7-11eb-84f5-a7c1d5c36df3.png)

#### 5.3.2 Joint PDFs

![image](https://user-images.githubusercontent.com/41487483/121728365-75f54400-caed-11eb-9935-66e24af94023.png)

* Joint PDFs are denoted as \\(f_{X,Y}(x,y)\\): probaility per unit area

    When X = Y, equal to a line, meaning X and Y are not joint PDFs.


#### 5.3.3 From the joint to the marginal

![image](https://user-images.githubusercontent.com/41487483/121731040-b73b2300-caf0-11eb-8a17-90bb4190224e.png)    

#### 5.3.4 Joint CDF

\\[
    F_{X,Y}(x,y) = P(X \leq x, Y \leq y) = \int\limits_{-\infty}^{y} \int\limits_{-\infty}^{x} f_{x,y}(s,t)dsdt 
\\]

### 5.4 Conditioning on a random variable and Bayers rule

#### 5.4.1 Conditional PDFs, given another r.v.

* \\(f_{X|Y}(x|y) = \frac{f_{X,Y}(x,y)}{f_Y(y)}\\), if \\(f_y(y) > 0\\)

    - \\(f_{X|Y}(x|y) \geq 0\\)

    - Think of value of Y as fixed at some y shape of \\(f_{X|Y}(\cdot|y)\\): slice of the joint

    - multiplication rule: 

        \\[
            f_{X|Y}(x,y) = f_Y(y) \cdot f_{X|Y}(x|y)    
        \\]

* \\(P(X \in A | Y = y) = \int_A f_{X|Y}(x/y)dx\\)

#### 5.4.2 Total probability and expectation theorems

* Anolog to the PMFs of discrete randome varable \\(p_X(x) = \sum\limits_y p_Y(y)p_{X|Y}(x|y)\\)

    For continuous r.v., there is 

    \\[
        f_X(x) = \sum_{-\infty}^{\infty} f_Y(y)f_{X|Y}(x|y)dy    
    \\]

* Anolog to the Expectation of discrete randome varable \\(E[X|Y=y] = \sum\limits_x x p_{X|Y}(x|y)\\)

    For continuous r.v., there is 

    \\[
        E[X|Y=y] = \int_{-\infty}^{\infty} xf_{X|Y}(x|y)dx    
    \\]

* Anolog to the discrete randome varable \\(E[X] = \sum\limits_y p_Y(y) E[X|Y=y]\\)

    For continuous r.v., there is 

    \\[     
        E[X] = \int_{-\infty}^{\infty} f_Y(y)E[X|Y=y]dy  
        \\\\ = \int_{-\infty}^{\infty} xf_X(x)dx             
    \\]

* Expected value rule

    \\[
        E[g(X)|Y=y] = \int_{-\infty}^{\infty} g(x)f_{X|Y}(x|y)dx    
    \\]

#### 5.4.3 Independence

\\[
    f_{X,Y}(x,y) = f_X(x)f_Y(y), for all x and y    
\\]

* \\(f_{X,Y}(x,y) = f_X(x)\\), for all y with \\(f_Y(y) > 0\\) and all x

* If X, Y are **independent**:

    \\[
        E[XY] = E[X]E[Y] \\\\
        var(X + Y) = var(X) + var(Y)
    \\]

    g(X) and h(Y) are also independent: \\(E[g(X)h(Y)] = E[g(X)] \cdot E[h(Y)]\\)

#### 5.4.4 The Bayes rule --- a theme with variations

* For discrete r.v., 

    - \\(p_{X|Y}(x|y) = \frac{p_X(x) p_{Y|X}(y|x)}{p_Y(y)}\\)

    - \\(p_Y(y) = \sum\limits_{x'} p_X(x')p_{Y|X}(y|x')\\)

* For continuous r.v., 

    - \\(f_{X|Y}(x|y) = \frac{f_X(x) f_{Y|X}(y|x)}{_Y(y)}\\)

    - \\(p_Y(y) = \int\limits f_X(x')f_{Y|X}(y|x')\\)

* One discrete and one continuous r.v.

    ![image](https://user-images.githubusercontent.com/41487483/121778872-456ae400-cb99-11eb-8fc6-d1cb9ea4f3f2.png)


## Unit 6 Further topics on random variables

### 6.1 Derived distributions 

#### 6.1.1 A linear function \\(Y =  aX + b\\)

* Discrete r.v. 

     \\(
        p_Y(y) = p_X(\frac{y-b}{a})
    \\)

* Continuous r.v.

    \\(
        f_Y(y) = \frac{1}{|a|}f_X(\frac{y-b}{a})
    \\)

    - A linear function of normal r.v. is normal

        If \\(X \sim N(\mu, \sigma^2)\\), then \\(aX + b \sim N(a\mu + b, a^2\sigma^2)\\)

#### 6.1.2 A general function \\(g(X)\\) of a continuous r.v.

**Two-step procedure:**

- Find the CDF of Y: \\(F_Y(y) = P(Y \leq y) = P(g(x) \leq y)\\) and the valid range of y

- Differentiate: \\(f_Y(y) = \frac{dF_Y(y)}{dy}\\)

1. A general formula for the PDF of \\(Y = g(X)\\) when *g* is monotomic

    \\[
        f_Y(y) = f_X(h(y))\left|\frac{dh(y)}{dy}\right|    
    \\]

    \\(x = h(y)\\) is the inverse function of \\(y = g(x)\\)

2. A nonmonotonic example \\(Y = X^2\\)

    - the discrete case: \\(p_Y(y) = p_X(\sqrt{y}) + p_X(-\sqrt{y})\\)

    - the continuous case: \\(f_Y(y) = f_X(\sqrt{y})\frac{1}{2\sqrt{y}} + p_X(-\sqrt{y})\frac{1}{2\sqrt{y}}\\)

3. A function of multiple r.v.'s: \\(Z = g(X,Y)\\)

    ![image](https://user-images.githubusercontent.com/41487483/122451427-69b72e00-cfa8-11eb-9aa5-b1c0855886d0.png)

### 6.2 Sums of independent vadom variables

#### 6.2.1 The distribution of \\(X + Y\\): the discrete case

Z = X + Y; X,Y independent, discrete known PMFs

\\[
    p_Z(z) = \sum\limits_x p_X(x)p_Y(z-x)    
\\]

**Dsicrete convoltion mechanics**

1. Flip the PMF of Y and put it underneath the PMF of X

2. Shift the flipped PMF by z 

3. Cross-multiply and add

#### 6.2.2 The distribution of \\(X + Y\\): the continous case

Z = X + Y; X,Y independent, continuous known PDFs

\\[
    f_Z(z) = \int\limits_x f_X(x)f_Y(z-x)dx    
\\]

- conditional on \\(X = x\\): 

    \\[
        f_{Z|x}(z|x) = f_Y(z-x)     
    \\]

    which can then be used to calculate Joint PDF of Z and X and marginal PDF of Z.

- Same mechanics as in discrete case

#### 6.2.3 The sum of independent normal r.v.'s

- \\(X \sim N(\mu_x, \sigma_x^2), Y \sim N(\mu_y, \sigma_y^2\\) **Independent**

    \\(Z = X + Y: \sim N(N(\mu_x + \mu_y,  \sigma_x^2 + \sigma_y^2))\\)

    **The sum of finitely many independent normals is normal**


### 6.3 Covariance (协方差)

#### 6.3.1 Definition

\\[
    cov(X,Y) = E[(X - E[X]) \cdot (Y - E(Y))]    
\\]

* If \\(X,Y\\) **independent: \\(cov(X,Y) = 0 \\)** 

*convers is not true!*


#### 6.3.2 Covariance properties

1. \\(cov(X,X) = var(X) = E[X^2] - (E[X])^2\\)

2. \\(cov(aX+b,Y) = a \cdot cov(X,Y)\\)

3. \\(cov(X,Y+Z) = cov(X,Y) + cov(X,Z)\\)

**Practical covariance formula:** 

\\[
    cov(X,Y) = E[XY] - E[X]E[Y]
\\]

#### 6.3.3 The variance of a sum of random variables

- two r.v.s

    \\[
        var(X_1 + X_2) = var(X_1) + var(X_2) + 2cov(X_1,X_2)    
    \\]

    *X,Y indepedent, then \\(var(X_1 + X_2) = var(X_1) + var(X_2)\\)*

- multiple r.v.s

    \\[
        var(X_1 + \dots + X_n) = \sum\limits_{i=1}^nvar(X_i) + \sum\limits_{(i,j):i \neq j}^n cov(X_i,X_j)  
    \\]

    *\\(\sum\limits_{(i,j):i \neq j}^n \\) contains \\((n^2 - n)\\) terms*

### 6.4 The correlation coefficient

\\[
    \rho(X,Y) = E\left[\frac{(X - E[X])}{\sigma_X} \cdot \frac{(Y - E[Y])}{\sigma_Y}\right] = \frac{cov(X,Y)}{\sigma_X \sigma_Y}
\\]

#### 6.4.1 Interpretation of correlation coeffecient

- Dimensionless version of covariance 

- Measure of the defree of "association" between X and Y

- Association does not imply causation or influence

- Correlation often refleces underlying, common, hidden factor


#### 6.4.2 Key properties of the correlation coeffecient

- \\(-1 \leq \rho \leq 1\\)

- **Independent** \\(\implies \rho = 0\\) "uncorrelated" (converse is not true)

- \\(|\rho| = 1 \Leftrightarrow\\) linearly related

- \\(cov(aX+b, Y) = a \cdot cov(X,Y) \implies \rho(aX+b,Y) = sigma(a)\rho(X,Y)\\)


### 6.5 Conditional expectation and variance as a random variable


#### 6.5.1 Conditional expecation

* **Definition**: \\(g(Y)\\) is the *random variable* that takes the value \\(E[X|Y=y]\\), if \\(Y\\) happens to take the value \\(y\\).

\\[
    E[X|Y] = g(Y)    
\\]

* **Law of iterated expectations**

\\[
    E[E[X|Y]] = E[g(Y)] = E[X]    
\\]

#### 6.5.2 Conditional variance

* Variance fundamentals

    \\[
        var(X) = E[(X - E[X])^2] \\\\
        var(X|Y=y) = E[(X - E[X|Y=y])^2|Y=y]
    \\]  

**var(X|Y) is the r.v. that takes the value var(X|Y=y), when Y=y**

* **Law of total variance**

    \\[
        var(X) = E[var(X|Y)] + var(E[X|Y])    
    \\]

    *var(X) = (average variability within sections) + (variability between sections)*

### 6.6 Sum a random number of indepedent r.v.'s

*Example of shopping*

- N: number of stores visited (N is a nonnegative integer r.v.)

- \\(X_i\\): money spent in store i 

    - \\(X_i\\) independent, identically distributed

    - independent of N

- Let \\(Y = X_1 + \dots + X_N\\)

#### 6.6.1 Expecatation of the sum

Based on the Law of iterated expectations:

\\[
    E[Y] = E[E[Y|N]] = E[N \cdot E[X]] = \cdot E[X]E[N]   
\\]

#### 6.6.2 Variance of the sum

Based on the Law of total variance: \\(var(Y) = E[var(Y|N)] + var(E[Y|N])\\):

\\[
    var(Y) = E[N]var(X) + (E[X])^2var(N) 
\\]


## Unit 7 Bayesian inferences

### 7.1 Introduction to Bayesian inference

#### 7.1.1 Basic concepts

1. Model building versus inferring unobserved variables

    \\[X = aS + W\\]

    S: signal; W: noise; a: medium (image a black box where S goes through and output X with W as noise)

    - Model building: known signal S, observe X -> infer a

    - Variable estimation: known a, observe X -> infer S

2. Hypothesis testing vs. estimation

    - Hypothesis testing

        * unknown takes one of few possible values

        * aim at small probability of incorrect decision

    - Estimation

        * numerical unknown(s)

        * aim at an estimate that is "close" to the true but unknown value

#### 7.1.2 The Bayescian inference framework

* Unknown \\(\Theta\\) - treated as a random variable **prior distribution: \\(p_{\Theta}\\) or \\(f_{\Theta}\\)**

* Observation \\(X\\) - observation model \\(p_{X|\Theta}\\) or \\(f_{X|\Theta}\\)

* Use appropriate version of the Bayes rule to find \\(p_{X|\Theta}(\cdot | X = x)\\) or \\(f_{X|\Theta} (\cdot| X = x)\\)

![image](https://user-images.githubusercontent.com/41487483/124636223-9617e900-de88-11eb-90fa-6c5b17f9f000.png)

* The output of Bayesian inference - **posterior distribution**

    - **Maximum a posterior probability (MAP)**:

        \\(p_{\Theta|X}(\theta^*|x) = \max\limits_{\theta} p_{\Theta|X}(\theta|x)\\)

        \\(f_{\Theta|X}(\theta^*|x) = \max\limits_{\theta} f_{\Theta|X}(\theta|x)\\)
    
    - **Conditional expectation: \\(E[\Theta|X = x]\\)** **Least Mean Square (LMS)**

    - estimate: \\(\hat{\theta} = g(x)\\) (number)

    - estimator: \\(\hat{\Theta} = g(X)\\) (random variable)

#### 7.1.3 Four cases

1. **Discrete \\(\Theta\\), discrete X**

    * values of \\(\Theta\\): alternative hypotheses

    \\[
        p_{\Theta|X}(\theta|x) = \frac{p_{\Theta}(\theta)p_{X|\Theta}(x|\theta)}{p_X(x)}    
    \\]

    \\[
        p_X(x) = \sum\limits_{\theta'}p_{\Theta}(\theta')p_{X|\Theta}(x|\theta')
    \\]

    * conditional prob of error: **Smallest under the MAP rule**
    
        \\[
            P(\hat{\theta} \neq \Theta|X = x)
        \\] 

    * overal probability of error: 
    
        \\[
            P(\hat{\Theta} \neq \Theta) = \sum\limits_{x} P(\hat{\Theta} \neq \Theta|X = x)p_X(x) = \sum\limits_{\theta}P(\hat{\Theta} \neq \Theta|\Theta = \theta)p_{\Theta}(\theta)
        \\] 


2. **Discrete \\(\Theta\\), Continuous X**

    \\[
        p_{\Theta|X}(\theta|x) = \frac{p_{\Theta}(\theta)f_{X|\Theta}(x|\theta)}{f_X(x)}    
    \\]

    \\[
        f_X(x) = \sum\limits_{\theta'}p_{\Theta}(\theta')f_{x|\Theta}(x|\theta')
    \\]

    - the same equation for conditional prob. of error

    - overall probability of error

        \\[
            P(\hat{\Theta} \neq \Theta) = \int\limits_{x} P(\hat{\Theta} \neq \Theta|X = x)f_X(x)dx = \sum\limits_{\theta}P(\hat{\Theta} \neq \Theta|\Theta = \theta)p_{\Theta}(\theta)
        \\] 

3. **Continuous \\(\Theta\\), Discrete X**

    \\[
        f_{\Theta|X}(\theta|x) = \frac{p_{\Theta}(\theta)p_{X|\Theta}(x|\theta)}{p_X(x)}    
    \\]

    \\[
        p_X(x) = \int\limits_{\theta'}f_{\Theta}(\theta')p_{x|\Theta}(x|\theta')d\theta'
    \\]

    - Inferring the unknown bias of a coin and **the Beta distribution**


4. **Continuous \\(\Theta\\), Continuous X**

    \\[
        f_{\Theta|X}(\theta|x) = \frac{f_{\Theta}(\theta)p_{X|\Theta}(x|\theta)}{p_X(x)}    
    \\]

    \\[
        f_X(x) = \int\limits_{\theta'}f_{\Theta}(\theta')p_{x|\Theta}(x|\theta')d\theta'
    \\]

    - Linear normal models: estimation of a noisy singal

    - Estimating the parameter of a uniform 

        \\(X\\): uniform \\([0, \Theta]\\)

        \\(\Theta\\): uniform \\([0, 1]\\)

    - Performance evaluation of an estimator \\(\hat{\Theta}\\)

        \\(E[(\hat{\Theta} - \Theta)^2|X = x]\\)

        \\(E[(\hat{\Theta} - \Theta)^2]\\)


Useful equation: 

\\[
    \int_0^1 \theta^\alpha(1-\theta)^\beta d\theta = \frac{\alpha!\beta!}{(\alpha + \beta + 1)!}    
\\]

### 7.2 Linear models with normal noise

#### 7.2.1 Recognizing normal PDFs

* Normal distribution: \\(X \sim N(\mu, \sigma^2)\\) 

    \\(f_X(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-(x-\mu)^2/2\sigma^2}\\)

* \\(f_X(x) = c e^{-(\alpha x^2 + \beta x + \gamma)}\\), \\(\alpha > 0\\) Normal with mean \\(-\beta/2\alpha\\) and variance \\(-1/2\alpha\\)

#### 7.2.2 Estimating a normal random variable in the presence of additive normal noise

\\(X = \Theta + W\\), \\(\Theta, W,N :(0,1), independent\\)

- \\( \hat{\theta} _{MAP} = \hat{\theta} _{LMS} = E[\Theta|X = x] = x/2\\)

- even with general means and variances:

    * posterior is normal

    * LMS and MAP estimators conincide

    * these estimators are "linear" of the form \\(\hat{\Theta} = aX + b\\)

#### 7.2.3 The case of multiple observations

\\(X_i = \Theta + W_1\\), \\(\Theta \sim N(x_0, \sigma_0^2)\\), \\(W_i \sim N(x_i, \sigma_i^2), \Theta, W_i\\) indepedent

* \\(\hat{\theta} _{MAP} = \hat{\theta} _{LMS} = E[\Theta|X = x] = \frac{\sum\limits _{i=0}^n\frac{x_i}{\sigma_i^2}}{\sum\limits _{i=0}^n\frac{1}{\sigma_i^2}}\\)

* Key conclusions

    - posterior is normal

    - LMS and  MAP estimates coincide

    - these estimates are "linear" of the form \\(\hat{\theta} = a_0 + a_1x_1 + \dots + a_nx_n\\)

* Interpretations

    - estimate \\(\hat{\theta}\\): weighted average of \\(x_0\\) (prior mean) and \\(x_i\\) (observations)

    - weights determined by variances

#### 7.2.4 The mean square error

* Performance measures

    - \\(E[(\Theta - \hat{\Theta})^2|X = x] = E[(\Theta - \hat{\theta})^2|X = x] = var(\Theta|X = x) = \frac{1}{\sum\limits _{i=0}^n \frac{1}{\sigma_i^2}}\\)

    - \\(E[(\Theta - \hat{\Theta})^2] = \int E[(\Theta - \hat{\Theta})^2|X = x] f_X(x) dx = \frac{1}{\sum\limits _{i=0}^n \frac{1}{\sigma_i^2}}\\)


### 7.3 Least mean squares (LMS) estimation

#### 7.3.1 In the absence of observations

* Least Mean Square formulation: minimize **Mean Squared Error (MSE)** \\(E[(\Theta - \hat{\theta})^2]: \hat{\theta} = E[\Theta]\\)

* \\(E[(\Theta - E[\Theta])^2]:var(\Theta)\\)

#### 7.3.2 LMS estimation of \\(\Theta\\) based on X

* Minimize **conditional mean square error**: \\(E[(\Theta - \hat{\theta})^2|X = x]: \hat{\theta} = E[\Theta|X = x]\\)

#### 7.3.3 LMS performance evaluation

* LMS estimate: \\(\hat{\theta} = E[\Theta|X=x]\\)

* Estimator: \\(\hat{\Theta} = E[\Theta|X]\\)

* Expected performance, once we have a measurement - **Conditional mean square error**

    \\(MSE = E[(\Theta - E[\Theta|X=x])^2|X=x] = var(\Theta|X=x)\\)

* Expected perfornamce of the design:

    \\(MSE = E[(\Theta - E[\Theta|X])^2] = E[var(\Theta|X)] = \int var(\Theta|X=x) \cdot f_X(x) dx\\) *Average of conditional variance*

* A good example

    ![image](https://user-images.githubusercontent.com/41487483/124714295-e1baa900-df01-11eb-8618-b411d877495e.png)

    ![image](https://user-images.githubusercontent.com/41487483/124714412-04e55880-df02-11eb-915d-996236e5958e.png)

#### 7.3.4 Properties of the estimation error in LMS estimation

Given Estimator: \\(\hat{\Theta} = E[\Theta|X]\\) and Error: \\(\tilde{\Theta} = \hat{\Theta} - \Theta\\)

* \\(E[\tilde{\Theta|X=x}] = 0\\)

* \\(cov(\tilde{\Theta},\hat{\Theta}) = 0\\)

* \\(var(\Theta) = var(\hat{\Theta}) + var({\tilde{\Theta}})\\)


### 7.4 Linear least mean squares (LLMS) estimation

*Motivation: Conditional expectation \\(E[\Theta|X]\\) maybe hard to compute/implement*

#### 7.4.1 LLMS formulation

Consider estimators of \\(\Theta\\) of the form \\(\hat{\Theta} = aX + b\\), minimize \\(E[(\hat{\Theta} - \Theta)^2] \implies E[(\hat{\Theta} - aX - b)^2] \\) 

#### 7.4.2 LLMS solution

![image](https://user-images.githubusercontent.com/41487483/124715231-0cf1c800-df03-11eb-9cf0-ec04d3cf70d4.png)

Minimize \\(E[(\hat{\Theta} - \Theta)^2]\\), that is \\(E[(\Theta - aX - b)^2]\\)

\\[
    \hat{\Theta}_L  = E[\Theta] + \frac{Cov(\Theta,X)}{var(X)}(X - E[X]) = E[\Theta] + \rho \frac{\sigma _\Theta}{\sigma_X}(X - E[X])   
\\]

\\(\rho\\) corelation coefficiency

**Remarks on the solution and on the error variance**

- Only means, variances, covariances matter (we do not need to know everything)

    \\(E[(\hat{\Theta}_L - \Theta)^2] = (1 - \rho^2)var(\Theta)\\)

#### 7.4.3 LLMS with multiple observations

- Consider the form \\(\hat{\Theta} = a_1X_1 + \dots + a_nX_n + b\\)

- Minimize \\(E[(a_1X_1 + \dots + a_nX_n + b - \Theta)^2]\\)

- Solve linear system in \\(b\\) and \\(a_i\\)

- if \\(E[\Theta|X]\\) is linear in X, then \\(\hat{\Theta} _{LMS} = \hat{\Theta} _{LLMS}\\)

- suppose general distributions with same mean, variances

    - \\(\hat{\theta} _{MAP} = \hat{\theta} _{LMS} = E[\Theta|X = x] = \frac{\sum\limits _{i=0}^n\frac{x_i}{\sigma_i^2}}{\sum\limits _{i=0}^n\frac{1}{\sigma_i^2}}\\)

    - \\(\hat{\Theta} _{LMS} = E[\Theta|X] = \frac{\frac{x_0}{\sigma _0^2} + \sum\limits _{i=i}^n\frac{X_i}{\sigma_i^2}}{\sum\limits _{i=0}^n\frac{1}{\sigma_i^2}} = \hat{\Theta} _{LLMS}\\)

### 7.5 Bayesian inference summary

![image](https://user-images.githubusercontent.com/41487483/124724545-5eeb1b80-df0c-11eb-964b-82371cd4799c.png)

</br>


## Unit 8 Limit theorems and clasic statistics

### 8.1 Inequalities, comvergence, and the Weak Law of Large Numbers

#### 8.1.1 Markov and Chebyshev inequality

1. **Markov inequality**

    "If \\(X \geq 0\\) and \\(E[X]\\) is small, then X is unlikely to be very large"

    \\[
        P(X \geq a) \leq \frac{E[X]}{a} \text{, for all }  a > 0 \text{ and }  X \geq 0
    \\]

2. **Chebyshev inequality**

    "If the variance is small, then X is unlikely to be too far from the mean"

    \\[
        P(|X - \mu| \geq c) \leq \frac{\sigma^2}{c^2} 
        \text{, for all }  c > 0 \text{ and }  X \text{ is a random variable with mean } \mu \text{ and variance } \sigma^2
    \\]

#### 8.1.2 The Weak Law of Large Numbers (WLLN)

\\(X_1, X_2, \dots\\) i.i.d.: infinite mean \\(\mu\\) and variance \\(\sigma^2\\)

\\[
    \text{Sample mean: } M_n = \frac{X_1 + \dots + X_n}{n}
\\]

- \\(E[M_n] = \mu\\)

- \\(Var(M_n) = \frac{\sigma^2}{n}\\)

- **WLLN:** for \\(\varepsilon > 0\\),

    \\[
        P(|M_n - \mu|) \geq \varepsilon = P \left( \left| \frac{X_1 + \dots + X_n}{n} - \mu\right| \geq \varepsilon \right) \to 0 \text{, as n} \to \infty
    \\]

- Interpreting the WLLN 

    - **Sample mean** \\(M_n\\) is unlikely to be far off from **true mean** \\(\mu\\)

    - **Sample mean** \\(M_n\\) is the **emperical frequency** of even \\(A\\), with \\(p = P(A)\\)

#### 8.1.3 Convergence in Probability

Sequence of random variables \\(Y_n\\), not necessarily independent

**Definition**: A sequence <a style="color:red;">\\(Y_n\\)</a> **converges in probability** to a certain number <a style="color:red;">a</a> if:

\\[
    \lim_\limits{n \to \infty} P(|Y_n - a| \geq \varepsilon) = 0   
\\]

*Almost all of the PMF/PDF of \\(Y_n\\) eventually gets concentrated (arbitrarily) close to a*

* Some properties - suppose that \\(X_n \to a, Y_n \to b\\)

    1. if *g* is continuous, then \\(g(X_n) \to g(a)\\)

    2. \\(X_n + Y_n \to a + b\\)

    3. \\(E[X_n]\\) <b>need not converge to a</b>


</br>

### 8.2 The Central Limit Theorem (CLT)

![image](https://user-images.githubusercontent.com/41487483/125804339-0461c83e-e397-488a-81ff-bfc51017512b.png)

#### 8.2.2 What exactly does the CLT say?

1. <strong>Theory</strong>

    \\(Z_n = \frac{S_n - n\mu}{\sqrt{n}\sigma}\\) and \\(Z \sim N(0,1)\\)

    - CDF of Z<sub>n</sub> converges to normal **CDF**

    - results for convergence of PDFs or PMFs (with more assumptions)

    - results without assuming that X<sub>i</sub> are identically distributed

    - results under "weak dependence"

    **In short, CLT applies to a sequence of random variables that do not need to be i.i.d.** 

2. <strong>Practice</strong>

    - The practiec of normal approximations:

        * treat Z<sub>n</sub> as if it were normal

        * treat S<sub>n</sub> as if normal: \\(N(n\mu, n\sigma^2)\\) as \\(S_n = \sqrt{n}\sigma Z_n + n\mu\\)

    - Can we use the CLT when n is "moderate"? 

        * usually, yes

        * symmetry and unimodality help


</br>

### 8.3 An introduction to classical statistics

#### 8.3.1 Overview 

- Inference using the Bayes rule:

    unknown \\(\Theta\\) and observation \\(X\\) are both random variables: Find \\(p_{\Theta|X}\\)

- Classical statistics: unknown **constant** \\(\theta\\)

    - Problem types in classical statistics

        * Hypothesis testing: \\(H_0: \theta = 1/2 \text{ vs. } H_1: \theta = 3/4\\)

        * Composite hypotheses: \\(H_0: \theta = 1/2 \text{ vs. } H_1: \theta \neq 1/2\\)

        * Estimation: design an estimator \\(\hat{\Theta}\\), to keep estimation error \\((\hat{\Theta} - \theta)\\) small.

#### 8.3.2 The sample mean and some terminology

- Estimating a mean

    * \\(X_1, \dots, X_n\\): i.i.d, mean \\(\theta\\), variance \\(\sigma^2\\)

    * **Sample mean** \\(= \hat{\Theta}_n = M_n = \frac{X_1 + \dots + X_n}{n}\\) 

- Properties and terminology

    * \\(E[\hat{\Theta}_n] = \theta\\)  <a style="color:red;">(unbiased)</a> for all \\(\theta\\)

    * WLLN: \\(E[\hat{\Theta}_n] \to \theta\\)  <a style="color:red;">(consistency)</a> for all \\(\theta\\)

    * Mean square error <a style="color:red;">(MSE)</a>: \\(E[(\hat{\Theta}_n - \theta)^2] = var(\hat{\Theta}_n) = \frac{\sigma^2}{n}\\)

#### 8.3.3 On the mean square error of an estimator

\\[
    E[(\hat{\Theta} - \theta)^2] = var(\hat{\Theta} - \theta) + (E[\hat{\Theta} - \theta])^2 = var(\hat{\Theta}) + (bias)^2   
\\]

- Sample mean estimator (\\(\hat{\Theta}_n = M_n\\)): \\(MSE = \frac{\sigma^2}{n} + 0\\)

- Zero estimator (\\(\hat{\Theta} = 0\\)): \\(MSE = 0 + \theta^2\\)

- \\(\sqrt{var(\hat{\Theta})}\\) is the <a style="color:red"> standard error </a>. 

    *Standard Error refers to sampling distribution, whereas standard deviation refers to sample distribution*

#### 8.3.4 Confidence intervals (CIs)

An \\(1 - \alpha\\) confidence interval is an interval \\([\hat{\Theta}^-, \hat{\Theta}^+]\\), for all \\(\theta\\)

\\[
    P(\hat{\Theta}^- \leq \theta \leq \hat{\Theta}^+)    
\\]

* **CI for the estimation of the mean**

    * \\(X_1, \dots, X_n\\): i.i.d, mean \\(\theta\\), variance \\(\sigma^2\\)

    * **Sample mean** \\(= \hat{\Theta}_n = M_n = \frac{X_1 + \dots + X_n}{n}\\) 

    * 95% CI: \\(\Phi(1.96) = 0.975 = 1 - 0.025\\)

        \\[
            P \left( \frac{|\hat{\Theta}_n - \theta|}{\sigma/\sqrt{n}}\right) \leq 1.96 \approx 0.95 \text{ (CLT) } \implies P \left(\hat{\Theta}_n - \frac{1.96\sigma}{\sqrt{n}} \leq \theta \leq \hat{\Theta}_n + \frac{1.96\sigma}{\sqrt{n}}\right)
        \\]

* **CI for the mean when \\(\sigma\\) is unknown**

    1. use upper bound on \\(\sigma\\)

        - for \\(X_i\\) Bernoulli: \\(\sigma \leq 1/2\\)

    2. use ad hoc estimate of \\(\sigma\\)

        - for \\(X_i\\) Bernoulli: \\(\sigma = \sqrt{\hat{\Theta}_n(1 - \hat{\Theta}_n)}\\)

    3. use sample mean estimate of the variance

        \\(\sigma^2 = E[(X_i - \theta)^2] \implies \frac{1}{n} \sum\limits_{i = 1}^n (X_i - \hat{\Theta}_n)^2 \to \sigma^2\\)

<hr>

- Two approximations involved here:

    - CLT: approximately normal

    - using estimate of \\(\sigma\\)

- correction for second approximation <a style="color:red">(t-tables)</a> used when *n* is small.

<hr>

#### 8.3.5 Other natural estimators

![image](https://user-images.githubusercontent.com/41487483/125932005-aaf38a3c-d0e4-41e8-9be0-7fd8c9896573.png)

#### 8.3.6 Maximum Likelihood (ML) estimation

* Pick <a style="color:red">\\(\theta\\)</a> that "makes data most likely"

    \\[
        \hat{\theta}_ {ML} = arg \max\limits_{\theta} p_X(x;\theta)    
    \\]

    <i>compare to maximum a posterior probability Bayesian posterior \\(p_{\Theta|X}(\theta^*|x) = \max\limits_{\theta}p_{\Theta|X}(\theta|x)\\)</i>

## Unit 9 The Bernoulli and Poisson process

### 9.1 The Bernoulli process 

#### 9.1.1 Definition

* A sequence of independent Bernoulli tirals, \\(X_i\\)

* At each trial, i:

    \\(P(X_i = 1) = P(\text{success at the ith trial}) = p\\)

    \\(P(X_i = 0) = P(\text{failure at the ith trial}) = 1 - p\\)

* Properties

    - \\(E[X_i] = p\\)

    - \\(var(X_i) = p*(1-p)\\)

* Key assumption

    - Independence

    - Time-homogeneity

#### 9.1.2 Stochastic processes

* A sequence of random variables \\(X_1, X_2, \dots\\)

* Sample space: \\(\Omega = \text{a set of infinite sequence of 0's and 1's}\\) 

#### 9.1.3. Number of successes/arrivals S in n time slots (Binomial distribution)

- \\(S = X_1 + X_2 + \dots + X_n\\)

- \\(P(S=k) = \binom{n}{k}p^k(1-p)^{n-k}\\), k = 0, 1, 2 ....

- \\(E[S] = np\\)

- \\(var(S) = np(1-p)\\)

#### 9.1.4 Time until the first success/arrival (Geometric distribution)

- \\(T_i = min \\\{i: X_i=1 \\\}\\)

- \\(P(T_1 = k) = (1-p)^(k-1)p\\), k = 1,2,...

- \\(E[T_1] = \frac{1}{p}\\)

- \\(var(T_1) = \frac{1-p}{p^2}\\)

#### 9.1.5 Independence, memorylessness, and fresh-start properties

* Fresh-start after time n (slots), after time T1

* Fresh-start after a random time N

    - N = time of 3rd sucess

    - N = first time that 3 successes in a row have been observed

* The process \\(X_{N+1}, X_{N+2}\\), ... is 

    - A Bernoulli process

    - independent of N, \\(X_1, X_2, \dots, X_N\\)

    *as long as N is determined "casually"*

#### 9.1.6 Time of the kth success/arrival

* \\(Y_k\\) = time of kth arrival

* \\(T_k\\) = kth inter-arrival time = \\(Y_k - Y_{k-1} \text{, } k \geq 2 \\)

* \\(Y_k = T_1 + \dots + T_k\\)

    - The process starts fresh after time T1

    - T2 is independent of T1: Geometric(p)

    - \\(E[Y_k] = \frac{k}{p}\\)

    - \\(var(Y_k) = \frac{k(1-p)}{p^2}\\)

    - PMF: \\(p_{Y_k}(t) = \binom{t-1}{k-1}p^k(1-p)^{t-k} \text{, } t = k, k +1, ..\\).

#### 9.1.7 Merging of independent Bernoulli processes

* \\(X_i\\): Bernoulli(p)

* \\(Y_i\\): Bernoulli(q)

* Merged process: \\(Z_i: g(X_i, Y_i)\\) Bernoulli(p + q - pq)

#### 9.1.7 Splitting of a Bernoulli process

![image](https://user-images.githubusercontent.com/41487483/126913885-cf7863e9-8053-4a4c-90d4-c6afc0585538.png)

#### 9.1.8 Poisson approximation to binomial 

* Interesting regime: large n, small p, <a style='color:red'> moderate λ = np</a>

* Number of arrivals S in n slots: \\(p_S(k) \to \frac{\lambda^k}{k!}e^{-\lambda}\\) (For fixed k = 0, 1...)

</br>

### 9.2 The Poison process

#### 9.2.1 Definition 

Poisson process is similar to Bernoulli process, but in a continuous time interval.

* Numbers of arrivals in disjoint time intervals are independent
 
    \\(P(k, \tau)\\) = Prob. of *k* arrivals in interval of duration \\(\tau\\)

* Small interval probabilities - For VERY small \\(\delta\\):

    \\[
        P(k, \delta) = \begin{cases} 1-\lambda\delta + O(\delta^2) & \quad \text{if } k = 0 \\\\
        \lambda\delta + O(\delta^2)  & \quad \text{if } k=1 \\\\
        0 + O(\delta^2) & \quad \text{if } k>1 \end{cases}
    \\]

    \\[
        P(k, \delta) \approx \begin{cases} 1-\lambda\delta & \quad \text{if } k = 0 \\\\
        \lambda\delta & \quad \text{if } k=1 \\\\
        0 & \quad \text{if } k>1 \end{cases}
    \\]

    **<a style='color:red'>λ: "Arrival rates" </a>**

#### 9.2.2 The Poisson PMF for the number of arrivals

* \\(N_{\tau}:\text{ arrivals in }[0, \tau]\\) 

* \\(N_\tau \approx Binomial(n,p)\\), \\(n = \frac{\tau}{\delta}\\), \\(p = \lambda\delta + O(\delta^2)\\)

* \\[
    P(k, \tau) = P(N_\tau =k) = \frac{(\lambda\tau)^ke^{-\lambda\tau}}{k!}, \text{k = 0, 1, 2,...}
\\]

* \\(E[N_\tau] \approx np \approx \lambda\tau\\)

* \\(var(N_\tau) \approx np(1-p) \approx \lambda\tau\\)

#### 9.2.3 The time \\(T_1\\) until the first arrival

Find the CDF: \\(P(T_1 \leq t) = 1 - P(T_1 > t) = 1 - P(0,t) = 1 - e^{-\lambda t}\\)

\\[
    f_{T_1}(t) = \lambda e^{-\lambda t} \text{, for } t \geq 0    
\\]

**<a style='color:red'>Exponential(λ) </a>**

#### 9.2.4 The time \\(Y_k\\) of the kth arrival

Two ways to derive: 

- Through CDF: \\(P(Y_k \leq y) = \sum\limits_{n=k}^{\infty}P(n, y)\\)

- More intuitive argument

    \\[
        f_{Y_k}(y)\delta \approx P(y \leq Y_k \leq y + \delta) \approx P(k-1, y)\lambda\delta
    \\]

**<a style='color:red'>Erlang distribution</a>**

\\[
    f_{Y_k}(y) = \frac{\lambda^k y^{k-1} e^{-\lambda y} }{(k-1)!} \text{, } y \geq 0  
\\]

#### 9.2.5 Memorylessness and the fresh-start property

* If we start watching at time *t*, we see Poisson process, independent of the history until time *t*. Then, time until next arrival follows exp(λ)

* Time between first and second arrival, \\(T_2 = Y_2 - Y_1\\) follows exp(λ)

* Similar for all \\(T_k = Y_k - Y_{k-1} \text{, } k \geq 2\\)

* \\(Y_k = T_1 + \dots + T_k\\) is sum of i.i.d. exponentials

    - \\(E[Y_k] = \frac{k}{\lambda}\\)

    - \\(var(Y_k) = \frac{k}{\lambda^2}\\)

#### 9.2.6 Bernoulli/Poisson relation

![image](https://user-images.githubusercontent.com/41487483/126948921-e39258a2-2396-4efb-8e13-4dbf605356f4.png)

|               | Poisson       | Bernoulli     |
| ------------- |:-------------:|:-------------:|
| Times of Arrival | Continuous | Discrete |
| Arrival Rate | λ per unit time | p per trial |
| PMF of # of arrivals | \\[P(k,\tau) = \frac{(\lambda\tau)^ke^{-\lambda\tau}}{k!} \\\\E[N_\tau] \approx \lambda\tau \\\\ var(N_\tau) \approx \lambda\tau\\] | \\[P_S(k) = \binom{n}{k}p^k(1-p)^{(n-k)} \\\\ \to \frac{\lambda^k}{k!}e^{-\lambda} \\\\ E[S] = np \\\\ var(S) = np(1-p) \\] |
| Interarrival Time Distr.| \\[f_{T1}(t) = \lambda e^{-\lambda t}\\] Exponential </br> \\[E[T_1] = 1/\lambda \\\\ var(T_1) = 1/\lambda^2\\] | \\[P_{T1} = (1-p)^{n-1}p\\] Geometric </br> \\[E[T_1] = 1/p \\\\ var(T_1) = \frac{1-p}{p^2}\\]|
| Time to k-th arrival | \\[f_{Y_k}(y) = \frac{\lambda^k y^{k-1} e^{-\lambda y}}{(k-1)!}\\] Erlang </br> \\[E[Y_k] = k/\lambda \\\\ var(Y_k) = k/\lambda^2\\]| \\[p_{Y_k}(t) = \binom{t-1}{k-1}p^k(1-p)^{t-k}\\] Pascal |

</br>

### 9.3 More on the Poisson process

#### 9.3.1 The sum of independent Poisson random variables

\\[
    P(k, \tau) = \frac{(\lambda\tau)^k e^{-\lambda\tau}}{k!}
\\]

We call it a Poisson random variable with parameters \\(\lambda\tau\\)

<a style='color:red'>The sum of independent Poisson random variables, with means/parameters \\(\mu\\) and \\(\nu\\) is Poisson with mean/parameter \\(\mu + \nu\\)</a>

#### 9.3.2 Merging independent Poisson processes

|               | 0 </br> \\(1 - \lambda_1\delta\\) | 1 </br> \\(\lambda_1\delta\\)| ≥ 2 </br> \\(O(\delta^2)\\)| 
|:--------------:|:-------------:|:-------------:|:--------------:|
| **0** \\(1 - \lambda_2\delta\\) | \\((1-\lambda_1\delta)(1-\lambda_2\delta)\\) | \\(\lambda_1\delta(1-\lambda_2\delta)\\) | - |
| **1** \\(\lambda_2\delta\\) | \\(\lambda_2\delta(1-\lambda_1\delta)\\) | \\(\lambda_1\lambda_2\delta^2\\) | - |
| **≥ 2** \\(O(\delta^2)\\)| - | - | - |

* 0 Arrivals \\(\approx 1 - (\lambda_1 + \lambda_2)\delta\\)

* 1 Arrivals \\(\approx (\lambda_1 + \lambda_2)\delta\\)

* ≥ 2 Arrivals \\(O(\delta^2)\\)

<a style='color:red'>Merging independent Poisson(λ1) and Poisson(λ1) result in Poisson(λ1 + λ2))</a>

#### 9.3.3 The time the first(last) light bulb burns out - min{X,Y,Z} and max{X,Y,Z} problem

Three lightbulbs have independent lifetimes X, Y, Z exponential(λ)

1. The expected time until first lightbulb burnout:

    * X, Y, Z: first arrivals in independent Poisson processes

    * Merged process: Poisson(3λ)

    * min{X, Y, Z}: 1st arrival in merged process \\(\to E[min] = 1/3\lambda\\)

2. The expected time until the last lightbulb burnout:

    * Merged process in different intervals

    \\[
        E[max] = \frac{1}{3\lambda} + \frac{1}{2\lambda} + \frac{1}{\lambda}
    \\]

#### 9.3.4 Splitting of a Poisson process

Split arrivals into two streams using independent coin flips of a coin with bias *q*

*Assume that coin flips are independent from the original Poisson process*

* <a style='color:red'>Resulting streams are Poisson with rate \\(\lambda q, \lambda (1-q)\\)</a>

* The splitted Poisson processes are <a style='color:red'>independent!</a>

#### 9.3.5 'Random incidence' in the Poisson process

1. Analysis

    ![image](https://user-images.githubusercontent.com/41487483/126982230-c8be5322-3130-43d5-8909-c9df592315a1.png)

2. Random incidence "Paradox" is not special to the Poisson process

    * Example: interarrival times, i.i.d., equally likely to be 5 or 10 mins. Then expected value of <a style='color:red'>k-th interarrival time </a> = 7.5

    * Show up at a <a style='color:red'>"random time"</a> 

        - P(arrival duaring a 5-minute interarrival interval) = 1/3

        - Expected length of interarrival interval during which you arrive ≈ 8.3

    * <a style='color:red'>Sampling method matters</a> - *Different sampling methods can give different results*

        - Average family size? (3 families with one person, 1 family with 6 persons)

            - look at a random family: 3/4x1 + 1/4x6

            - looat at a random persons's family: 3/9x1 + 6/9x6

        - Average bus occupancy?

        - Average class size?

### 9.4 Additional theoretical background

#### 9.4.1 Poisson versus normal approximation to the binomial

We have seen that a binomial random variable with parameters *n* and *p* can be approximated by a normal random variable (central limit theorem) but also by a Poisson random variable. Are these two facts contradictory? Fortunately not; the two approximations apply to different regimes:

1. if we fix *p* and let \\(n \to \infty)\\), we are in the setting where the **central limit theorem** applies.

2. If we let \\(n \to \infty)\\), \\(p \to 0)\\), while keeping the product *np* fixed, the Poisson approximation applies.

3. If *p* is very small but *np* is very large, then two approximations agree.

#### 9.4.2 Sums of a binomial and a Poisson-distributed number of Bernoulli r.v.'s

Let \\(X_1,X_2,...\\) be independent Bernoulli random variables with parameter *p*, and *N* be a random variable that takes integer values and is independent of \\(X_i, i = 1,2, \dots\\) Let \\(Y=X_1+X_2+ \dots +X_N\\) for positive values of *N*, and let \\(Y =0\\)  when \\(N=0\\).

- If *N* is binomial with parameters *m* and *q*, then *Y* is binomial with parameters *m* and *pq*.

    ![image](https://user-images.githubusercontent.com/41487483/127369301-0884ba53-e79c-4cd9-8545-368f7ef5c03f.png)

- If *N* is poisson with parameters \\(\lambda\\), then *Y* is Poisson with parameter \\(\lambda\\).

    ![image](https://user-images.githubusercontent.com/41487483/127369385-7d06f2f1-2866-4949-b342-933fe8bfe6d2.png)


#### 9.4.3 Sums of a geometrically-distributed number of geometric and exponential r.v.'s

Let *N* be a geometric random variable with parameter *q*, and let \\(X_1, X_2, \dots\\) be random variables that are independent and independent of *N*. Let \\(Y=X_1+\dots+X_N\\).

- If \\(X_i\\) is geometric with parameter *p*, then *Y* is geometric with parameter *pq*

    ![image](https://user-images.githubusercontent.com/41487483/127370021-c2299c8b-8107-4826-b1df-048ec9bdde81.png)

- If \\(X_i\\) is exponential with parameter \\(\lambda\\), then *Y* is exponential with parameter \\(\lambda q\\)

    ![image](https://user-images.githubusercontent.com/41487483/127370100-fc323f23-7d82-4b50-aa98-2fc0bb17c31c.png)