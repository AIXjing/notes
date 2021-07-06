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

* Expected performance, once we have a measurement: 

    \\(MSE = E[(\Theta - E[\Theta|X=x])^2|X=x] = var(\Theta|X=x)\\)

* Expected perfornamce of the design:

    \\(MSE = E[(\Theta - E[\Theta|X])^2] = E[var(\Theta|X)] = \int var(\Theta|X=x) \cdot f_X(x) dx\\) *Average of conditional variance*

#### 7.3.4 Properties of the estimation error in LMS estimation

Given Estimator: \\(\hat{\Theta} = E[\Theta|X]\\) and Error: \\(\tilde{\Theta} = \hat{\Theta} - \Theta\\)

* \\(E[\tilde{\Theta|X=x}] = 0\\)

* \\(cov(\tilde{\Theta},\hat{\Theta}) = 0\\)

* \\(var(\Theta) = var(\hat{\Theta}) + var({\tilde{\Theta}})\\)


### 7.4 Linear least mean squares (LLMS) estimation

#### 7.4.1 LLMS formulation

\\(\hat{\Theta} = aX + b\\), minimize \\(E[(\hat{\Theta} - \Theta)^2]\\)


#### 7.4.2 LLMS solution

Minimize \\(E[(\hat{\Theta} - \Theta)^2]\\), that is \\(E[(\Theta - aX - b)^2]\\)

\\[
    \hat{\Theta_L}  = E[\Theta] + \frac{Cov(\Theta,X)}{var(X)}(X - E[X]) = E[\Theta] + \rho \frac{\sigma_\Theta}{\sigma_X}(X - E[X])   
\\]

\\(\rho\\) corelation coefficiency

- Only means, variances, covariances matter (we do not need to know everything)

\\[
    E[(\hat{\Theta} _L - \Theta)^2] = (1 - \rho^2)var(\Theta)
\\]

- LLMS with multiple observations