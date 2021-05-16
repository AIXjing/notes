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