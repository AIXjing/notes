# Probability - The Science of Uncertainty and Data (2021)

Use the course to re-build my statistics knowledge.

[The course link](https://www.edx.org/course/probability-the-science-of-uncertainty-and-data)

[The Book](https://ece307.cankaya.edu.tr/uploads/files/introduction%20to%20probability%20(bertsekas,%202nd,%202008).pdf)

## Unit 1 Sample Space and Probability

### 1 Fundamental laws

**Sample space** - A set of outcomes
       
#### 1.1 Probabilistic models

**Probability Law**

* Nonnegativity
\\(P(A) \geq 0 \\)

* Additivity: A and B are disjoint, then the probability of their unions satisfies \\(P(A \cup B) = P(A) + P(B)\\)

* Normalization
  \\( P( \Omega ) = 1 \\), \\(\Omega \\) is the entire sample space.

**Discrete Probability Law**

If the sampe sapce consist of a finite number of possible outcomes,
\\[ 
    P({s_1, s_2, ...., s_n}) = P(s_1) + P(s_2) + ...... P(s_n)
\\]

**Discrete Uniform Probability Law**

If the sample space consists of n possible outcomes which are equally likely (i.e., all single-element events have the same probability),
\\[ 
    P(A) = \frac{number of elements of A}{n}
\\]


*Some properties of Probabily Laws*
1. If \\( A \subset B \\), then P(A) \\( \leq \\) P(B)
2. \\( P(A \cup B ) = P(A) + P(B) - P(A \cap B) \\)
3. \\( P(A \cup B ) \leq P(A) + P(B) \\)
4. \\( P(A \cup B \cup C) = P(A) + P(A^c \cap B) + P(A^c \cap B^c \cap C) \\)

<br> 

**Uniform Probability Law**

Probability = area

**Countable aditivity axiom** for Discrete but infinite sample space
\\[
    P(A_1 \cup A_2 ...... \cup A_i) = P(A_1) + P(A_2) + ...... + P(A_i)
\\]

<br>
<br>

#### 1.2 Sets

A collection of distinc elements 

* finite: e.g. {a, b, c, d}

* infinite: the reals (R)

* \\( \Omega \\) - the universal set

* Ø - empty set

*What are reals?*

*The reals include rational numbers (terminating decimals and non-terminating recurring decimals and irrational numbers (non-terminating non-reccuring decimals*

<br>

**Countable and uncountable infinite sets**

* Countable

    * integers, pairs of positive integers, etc.

    * rational numbers q. with 0 < q < 1

* Uncountable - *continuous numbers*

    * the interval [0, 1]

    * the reals, the plane, etc.

    *How to prove the reals are uncountable - "Control's diagonalization argument"*

<br>

**De Morgans' Law**

* \\( (S \cap T)^c = S^c \cup T^c \\) and \\( (S \cup T)^c = S^c \cap T^c \\)

* \\( (S^c \cap T^c)^c = S \cup T \\)

<br>
<br>

## Unit 2 Conditioning and independence

Refer to Section 1.3 - 1.5 in the textbook

### 2.1 Conditional and Bayes' Rules

#### 2.1.1 Conditional probability

**The definition of conditional probability**

P(A|B) = "probability of A, given that B occurred"

\\[
    P(A|B) = \frac{P(A \cap B )}{P(B)}
\\]

defined only when P(B) > 0

Conditional probabilities obey the same axioms.

**Models base on conditional probabilities**

![image](https://user-images.githubusercontent.com/41487483/117574884-993c6600-b0df-11eb-9125-c5501b77d001.png)


**The multiplication rule**

\\(P(A \cap B) = P(B)P(A|B) = P(A)P(B|A)\\)

\\(P(A^c \cap B \cap C^c) = P(A^c \cap B) P(C^c|A^c \cap B) = P(A^c) P(B|A^c) P(C^c|A^c \cap B)\\)

\\(P(A_1 \cap A_2...\cap A_n) = P(A_1) \sqcap_{i=2}^n P(A_i|A_1 \cap A_2...\cap A_i)\\)