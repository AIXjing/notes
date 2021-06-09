# Statistics with Python

## 1 Introduction to Probability and Statistics

### 1.1 Probability Theory

Use Python to simulate coin tossing problem,

```py
# Generate the sum of k coin flips, repeat that n times
def generate_counts(k=1000, n=100):
  X=2*(np.random.rand(k,n)>0.5)-1 # generate a kXn matrix of +-rando
  S=np.sum(X, axis=0)
  return S
coins_flip = generate_counts()

# plot a histogram
plt.style.use('ggplot')
plt.hist(coins_flip, 10, range = [-400, 400])
plt.show
```

`np.random.rand(k,n)>0.5` generate a True/False (k,n) matrix, but it transforms to an integer matrix with `2*`

* In most cases, we can **approximate** probabilities using simulations (Monte-Carlo simulations)

* However, calculating the probabilities is better because it provides a precise answer and is much faster than Monte-Carlo simulations.

### 1.2 What is statistics?

**Statistics is about analyzing real-world data and drawing conclusions.**

**The logical of Statistic inference**

To answer the question "whether the coin is biased given 570 heads after tossing 1000 times",

1. Suppose that the coin is fair

2. Use **probability theory** to compute the probability of getting at least 570 (or 507) heads

3. If this probability is very small, then we can reject with confidence the hypothesis that the coin is fair.

    *Given \\(x_i = -1\\) for tails and \\(x_i = +1\\), we looked at the sum \\(S_k = \sum_{i=1}^{k} x_i\\)*

    *If number of heads = 570, then \\(S_{1000} = 140\\)*
    
    *It is known that it is unlikely that \\(|S_k| > 4 \sqrt{k}\\), that is \\(|S_{1000}| > 4 sqrt{1000} \approx 126.5\\)*

    ```py
    from math import sqrt
    4*sqrt(1000)
    ```

    *Therefore, it is very unlikely that the coin is unbiased. -> the coin is probably biased.*

    
### 1.3 Three card puzzle

**Three cards in a hat**

Suppose we have three cards in a hat:

  - 'R''B' - one card is painted blue on one side and red on the other

  - 'R''R' - one card is painted blue on both sides

  - 'B''B' - one card is painted red on both sides


I pick one of the three cards at random, flip it to a random side, and place it on the table. If the other side of the card has a different color I pay you $1; if not you pay me $1.

**Monte Carlo simulation**

```py

red_bck="\x1b[41m%s\x1b[0m" 
blue_bck="\x1b[44m%s\x1b[0m"
red=red_bck%'R'
blue=blue_bck%'B'
Cards=[(red,blue),(red,red),(blue,blue)]
counts={'same':0,'different':0}

for j in range(50):
    i=int(np.random.rand()*3.) # Generate a random integer in an array [0,1,2] indicating three cards
    side=int(np.random.rand()*2.) # Generate either 0 or 1 indicating the color
    C=Cards[i]
    if(side==1): # select which side to be "up" ('red' is "up")
        C=(C[0],C[1]) # two sides of the selected cards
    same = 'same' if C[0]==C[1] else 'different' # count the number of times the two sides are the same or different.
    counts[same]+=1
    print(''.join(C)+' %-9s'%same, end='')
    if (j+1)%5==0:
    print()
print()
print(counts)
```

## 2 Elements, sets and membership

### 2.1 Basic concepts

**Common sets**

- Intergers {..., -2, -1, 0, 1, 2, ...} \\(Z\\)

- Naturals {..., 0, 1, 2, 3, ...} \\(N\\)

- Positives {1, 2, 3, ...} \\(P\\)

- Rationals {interger ratios m/n, \\(n \neq 0\\)} \\(Q\\)

- Reals {...Google...} \\(R\\)

* The **order** and **repetition** do no matter: 

  - {0,1} = {1,0}

  - {0,1,1,1} = {0,1}


**Special sets**

  - Empty set: \\(x \notin \varnothing\\)

  - Universal set: \\(\forall x \in \Omega\\)


* Define a set in python
  
  - Define a set: `set1={1,2}` or `set2=set({2,3})`

  - Define an empty set: `set()` or `set({})`

* Membership - `in` and `not in`

* Test empty - `not`

```py
S = set()
not S
#Output: True
```

* Set size - `len()`

### 2.2 Basic sets

#### 2.2.1 Sets within Sets

{\\(x \in A | .... \\)} = {elements in A such that}

* Integer Intervals

  \\(N = \\\{ x \in Z | x \geq 0 \\\}\\), \\(P = \\\{ x \in Z | x > 0 \\\} \\)

* Real intervals

  \\([a,b] = \\\{ x \in R | a \leq x \leq b \\\}\\)

  \\((a,b) = \\\{ x \in R | a < x < b \\\}\\)


* Divisibility

  ![image](https://user-images.githubusercontent.com/41487483/119231729-a49d8180-bb22-11eb-9a44-901751904204.png)

  **Sets of Multiples** 
  
  \\(m \in Z\\), \\(_m Z = \\\{ i \in Z : m| i \\\}\\)

  *Even numbers*: \\(_2 Z = \\\{ ..., -4, -2, 0, 2, 4, ... \\\} = E\\) 

**Python syntax**

  - {0,...,n-1}: `range(n)`

  - {m,...,n-1}: `range(m,n)`

  - {m, m+d, m+2d, ...} < n-1: `range(m, n, d)`

  ```py
  print(set(range(3)))
  #Output: {0, 1, 2}

  print(set(range(2,5)))
  #Output: {2, 3, 4}

  print(set(range(2,12,3)))
  #Output: {2, 5, 8, 11}
  #Return type range, but conver to set if print
  ```

#### 2.2.2 Visualization - Venn Diagram

```py
import matplotlib.pyplot as plt
import matplotlib_venn as venn
S = {1, 2, 3}
T = {0, 2, -1, 5}
venn.venn2([S, T], set_labels=('S','T'))
plt.show()

#for 3 sets: venn.venn3([S,T,U], set_labels=(’S’,’T’,'U'))
```

### 2.3 Relations

#### 2.3.1 Number relations

* Equality - = or ≠

* Intersection - two sets share at least one common element

  Disjoint - no shared elements

* Subsets - \\(A \subseteq B\\) 

  superset - \\(B \supseteq A\\) 

  \\[
    P \subseteq N \subseteq Z \subseteq Q \subseteq R
  \\]

  strict subset - if \\(A \subseteq B\\) and \\(A \neq B\\), A is a strict subset of B, denote \\(A \subset B\\); conversely, A is a strict superset of B, \\(B \supset A\\)

#### 2.3.2 Belongs to (\\( \in \\)) vs. Subsets of (\\(\subseteq \\))

- \\( x \in A \\): element x belongsto set A

  \\( 0 \in \\\{0,1\\\} \\)

- (\\( A \subseteq B \\)): A is a subset of B

   \\( \\\{ 0 \\\} \subseteq \\\{0,1\\\} \\)

#### 2.3.3 Python syntaxt

- Check equality and disjoint

  `==`, `!=`, `.isjointed()`

  ```py
  S1={0,1}; S2=set({0,1}); S3={1,0,1}; T={0,2}

  # Equality
  S1 == T
  #Output: False
  S1 == S2
  S1 == S3
  #Output: True

  # Inequality
  S1 != S2

  # Disjoint 
  S1.isdisjoint(T)
  S1.isdisjoint({2})

  ```

- Check subsets and supersets

  `<=` or `issubset` for \\(\subseteq \\) and `<` for \\(\subset \\) 

  `>=` or `issuperset` for \\(\supseteq \\) 

  ```py
  zero = {0}; zplus = {0,1}; zminus = {0, -1}

  print(zminus <= zplus)
  #Output: False
  print(zminus >= zplus)
  #Output: False

  zero.issubset(zminus)
  #Output: True
  ```

### 2.4 Operations

#### 2.4.1 Intersection and complement

* Commutative: \\(A \cap B = B \cap A\\), \\(A \cup B = B \cap A\\)

* Associative: \\((A \cap B) \cap C = A \cap (B \cap C)\\), \\((A \cup B) \cup C = A \cup (B \cup C)\\)  

* Distributive: \\(A \cap (B \cup C) = (A \cap B) \cup (A \cap C)\\), \\(A \cup (B \cap C) = (A \cup B) \cap (A \cup C)\\) 

* De Morgan \\((A \cap B)^c = A^c \cup B^c\\), \\((A \cup B)^c = A^c \cap B^c\\)

![image](https://user-images.githubusercontent.com/41487483/120278375-7d2e7d80-c2b5-11eb-8206-7da3043f30d1.png)

#### 2.4.2 Set Difference A-B

  * \\(A-B = \\\{ x: x \in A \wedge x \notin B \\\} = A \cap B^c\\) 

  ![image](https://user-images.githubusercontent.com/41487483/120279116-5ae92f80-c2b6-11eb-8c10-01913e85e304.png)

  * Symmetric Difference

    The symmetric differene of two sets is the set of elements in exactly one set. 

    \\(A bigtriangleup B = \\\{x: x \in A \wedge x \notin B  \vee x \in B \wedge x \notin A \\\} \\)

    ![image](https://user-images.githubusercontent.com/41487483/120279841-3772b480-c2b7-11eb-851c-a33544dd75f7.png)

#### 2.4.3 Python Syntax 

**Union and Intersection**

  * Union \\(\cup\\): `|` or `union`

  ```py
  A = {1,2}
  B = {2,3}

  print(A|B)

  C = A.union(B)
  print(C)
  ```

  * Intersection \\(\cap\\): `&` or `intersection`

  ```py
  print(A&B)

  C = A.intersection(B)
  print(C)
  ```

**Set- and Symmetric-Difference**

* Set difference: `-` or `difference`

  ```py
  A = {1,2}
  B = {2,3}

  A - B

  C = B.difference(A)
  print(C)
  ```

* Symmetric difference: `^` or `symmetric_difference`

  ```py
  A^B

  C = B.symmetric_difference(A)
  print(C)
  ```

#### 2.4.4 Caetesian products

  * **Set**: Order and repetition do not matter {a,b,c} = {b,a,c}

  * **Tuple**: Both order and reperition matter (a,b,c) ≠ (b,a,c) and (a,a,a) ≠ (a)

    - **n-tuple**: Tuple with n elements

    - **2-tuple**: Ordered pair (a,b)

##### **Cartesian products**

The cartesian product of A and B is the set AxB of ordered pairs (a,b) where a \\(\in A\\) and b \\(\in B\\)

\\[
  A \times B = \\\{(a,b): a \in A, b \in B \\\}  
\\]

- \\(A \times A\\) denotes \\(A^2\\)

- \\(R^2 = \\\{(x,y): x,y \in R\\\} \\) - **Cartesian Plane**

- \\(A, B \\subseteq R \\) then \\(A \times B \\subseteq R^2 \\) - **Rectangle**

- \\(A \times B = \\{(x,y): x \in [0,2], y \in [1,4] \\}\\), where A = [0,2] and B = [1,4]

  ![image](https://user-images.githubusercontent.com/41487483/120438263-6fdec500-c381-11eb-9064-8bdb146ea448.png)

1. **Discrete sets**

  ![image](https://user-images.githubusercontent.com/41487483/120438592-dcf25a80-c381-11eb-9f05-c377799e2def.png)


2. **Tables**

  *Tables are Cartesian products*

  ![image](https://user-images.githubusercontent.com/41487483/120439120-73bf1700-c382-11eb-9e5f-e3c4ced0d0a9.png)

3. **Cartesian product of 3 sets** 
  
  A x B - 2D
  
  A x B x C - 3D

4. **Sequence** 
  
    Sequence is tuples just without '()' and some times without ','

##### **Cartesian products with Python**

  ```py
  from itertools import product

  Faces = set({'J', 'Q', 'K'})
  Suits = {'♢','♡'}
  for i in product(Faces, Suits):
  print(i)
  ```

#### 2.4.5 Russell's Paradox

![image](https://user-images.githubusercontent.com/41487483/120651186-ca118000-c47e-11eb-9f1f-d1e85e4d090b.png)


## 3. Counting

### 3.1 Set Size

#### 3.1.1 Basic concepts

The number of elements in a set S is called its **size**, or **cardinality** (基数), denoted |B| or # S.

in Python 

- Size: `len`, i.e., `len({-1, 1})`

- Sum: `sum`, i.e., `sum({-1, 1})`

- minimum: `min`, i.e., `min({-1, 1})`

- maximum: `max`, i.e., `max({-1, 1})`


#### 3.1.2 Disjoint

- Additional rule (for disjoint): 

  \\(A \cap B = \varnothing\\): \\(|A| + |B| = |A \cup B\\)|

- Subtraction rule (for complement):

  \\(A \subseteq B \implies B = A \cup (B - A) \implies |B| = |A| + |B - A|\\) 

#### 3.1.3 General Unions

**Principle of Inclusion-Exclusion (PIE)**

- Two sets

\\[
  |A \cup B| = |A| + |B| - |A \cap B |
\\] 

- Three sets
 \\[
   |A \cup B \cup C| = |A| + |B| + |C| - |A \cap B |- |A \cap C| - |B \cap C| + |A \cap B \cap C| 
  \\]

- n sets

#### 3.1.4 Cartesian Products

**Product Rule** - the size of a Cartesian Product is the product of the set sizes. (multiplication)

\\[
  |A \times B| = |A| \times |B|
\\]

#### 3.1.5 Cartesian Powers

Applications: 

- Binary strings: \\(\\\{0,1\\\}^n = |\\\{0,1\\\}|^n = 2^n\\)

- Subsets

  The *power set* of S, \\(P(S)\\), is the collection of all subsets of S.

  \\[
      P(\\\{ a, b \\\}) = \\\{ \\\{ \\\}, \\\{ a \\\}, \\\{ b \\\}, \\\{a, b \\\} \\\}  
  \\]

  The size of the power set is the power of the set size.

  \\[
    |P(S)| = |\\\{0,1\\\}|^{|S|} = 2^{|S|} 
  \\]

  \\(P(P(S))\\) - set of subsets of P(S)

  \\[
    |P(P(S))| = 2^{|P(S)|} = 2^{2^{|S|}}
  \\]

- Functions

  Functions from A to B: \\(B^A\\), # = \\(|B|^{|A|}\\)

  - Binary functions

    Binary functions of n binary variables: Functions from \\(\\\{0 ,1 \\\}^n \\) to \\( \\\{0 ,1 \\\} \\). That is \\( \\\{0,1 \\\}^{{ \\\{0,1\\\} }^{n}} \\)

    #= \\(2^{2^n}\\) **Double exponntial**

  *Exponential Growth*

  - \\(A^k\\): `itertools.product(A, repeat = k)`

  - \\(n^k\\): `n**k`

  ```py
  import itertools 
  set(itertools.product({1,2, 3}, repeat = 2))

  #Exponent
  print(3**2)
  ```

### 3.2 Variations

Variable length 

Take an example of PIN: #3-5 digit PINs

### 3.3 Counting trees

-  Cartesian products as Trees

![image](https://user-images.githubusercontent.com/41487483/120917627-800fe080-c6b0-11eb-8fe2-8edc7186f27c.png)

- Trees are more general products

For example, in a university, there are 3 departments, and each department has 2 different courses. Therefore there are 6 courses in total. 

**Path from Sources to Destination**

![image](https://user-images.githubusercontent.com/41487483/120917920-0da00000-c6b2-11eb-9016-1182865eb950.png)


## 4 Permutations and combinations

### 4.1 Permutations

#### 4.1.1 Basic concept and application

- **n factorial = n!**

- 0! = 1

- **Stirling's approximation**

  \\[
    n! \sim \sqrt{2 \pi n} \left(\frac{n}{e}\right)^n 
  \\]

#### 4.1.2 Partial Permutations

* permutations of k out of n objects: k-permutaitons of n

  \\(n \cdot (n-1) \cdot (n-2) \cdot \dotsb \cdot(n-k+1) = \frac{n!}{(n-k)!} \newcommand*{\defeq}{\stackrel{\text{def}}{=}} (n)^{\underline{k}}\\)

  kth falling power of n, also denoted \\(P(n,k)\\)


### 4.2 Combinations

* Sequences with k 1's

  \\(\binom{[n]}{k} \\) - collection of k-subsets of [n] = {1,2,...,n}

  corresponds to n-bit sequences with k 1's

  two interpretations

![image](https://user-images.githubusercontent.com/41487483/121245332-3554bb00-c8a0-11eb-82e7-5af3f606d8a9.png)

* Number of n-bit sequences with k 1's: \\(\binom{n}{k}\\) 

#### 4.2.1 Binomial coefficients

\\[
  \binom{n}{k} = \frac{n^{\underline{k}}}{k!} = \frac{n!}{k!(n-k)!}
\\] 

  - \\(\binom{n}{k} = \binom{n}{n-k}\\)

  - recursive: \\(\binom{n}{k} = \frac{n}{k} \cdot \binom{n-1}{k-1}\\)

    \\[
      \binom{n}{k} \cdot k = n \cdot \binom{n-1}{k-1}  
    \\]

  - \\(\sum\limits_{i=0}^{n} \binom{n}{i} = 2^n\\)

#### 4.2.2 Binomial Theorem

* Pascal's identity

\\[
  \binom{n+1}{k} = \binom{n}{k} + \binom{n}{k-1}  
\\]

* Pascal's triangle

  ![image](https://user-images.githubusercontent.com/41487483/121404277-187dbd80-c95c-11eb-9214-7cdbdbe4dfc1.png)


* **Binomial Theorem**

  \\[
    (a+b)^n = \sum\limits_{i=0}{n} \binom{n}{i}a^{n-i}b^i
  \\]

  For example, \\((a+b)^4 = a^4 + 4a^3b + 6a^2b^2 + 4ab^3 + b^4\\)

  Think of select # b from n set of {a,b}: 

  \\[
    (a+b)^n = \binom{n}{0}a^n + \binom{n}{1}a^{n-1}b + \dots + \binom{n}{n}b^n = \sum\limits_{i=0}^{n}\binom{n}{i}a^{n-i}b^i   
  \\]

  - Polynomial coefficient

    \\[
      (1+x)^n = \sum\limits_{i=0}^{n}\binom{n}{i}x^i  
    \\]

  - Taylor expansion

    \\[
      e^x = \sum\limits_{i=0}^{\infty} \frac{x^i}{i!}
    \\]

    derived from \\((1 + \frac{x}{n})^n = \sum\limits_{i=0}{n} \binom{n}{i} \left(\frac{x}{n}\right)^i\\)

  - Binomial distribution

    \\[
      \sum\limits_{i=0}^{n} \binom{n}{i} p^{n-1}(1-p)^i = (p + (1 - p))^n = 1^n = 1  
    \\]
  
  #### 4.2.3 Multinomial coefficients

  \\[
    \frac{n!}{k_1! \cdot k_2! \cdot k_3!} \triangleq \binom{n}{k_1, k_2, k_3}, (k_1 + k_2 + k_3 = n)
  \\]

  * Multinomial theorem

  \\[
    (a_1 + a_2 + \dots + a_m)^n = \sum\limits_{k_1 + k_2 + \dots + k_m = n \\\\ k_1, k_2, \dots, k_m \geq 0} \binom{n}{k_1,k_2,\dots, k_m}  \prod\limits_{t=1}^{m} a_t^{k_t}
  \\]

  * Sum of Multinomialas

  \\[
    m^n = (1 + 1 + \dots + 1)^n = \sum\limits_{k_1 + k_2 + \dots + k_m = n \\\\ k_1, k_2, \dots, k_m \geq 0} \binom{n}{k_1,k_2,\dots, k_m}
  \\]

### 4.3 Stars and bars

#### 4.3.1 Basic applications

* k terms adding to n

  #ways to write n as a sum of k positive integers, when order matters: \\(\binom{n-1}{k-1}\\)

* Any Sum to n

  #ways to write n as a sum of (any # of) positive integers: \\(2^{n-1} = \sum\limits_{i=0}^{n-1}\binom{n-1}{i}\\)

* Nonnegative terms

  #ways to write n as a sum of k nonnegative integers: \\(\binom{n+k-1}{k-1}\\)

* Simple example

  4-letter words (order doesn't matter): #a + #b + ... + #z = 4 \\(\implies \binom{4+26-1}{26-1} = \binom{29}{25} = \binom{29}{4}\\)

#### 4.3.2 More applications

* #k positive adding to n = #k nonnegative adding to n-k

  \\[
    \binom{n-1}{k-1} = \binom{n-k+(k-1)}{k-1}  
  \\]

* #k nonnegative adding to ≤ n = #k+1 nonnegative adding to n

  \\[
    \binom{n+k}{k} = \binom{n+(k+1)-1}{(k+1)-1}
  \\]

  *need to use Pascal's triangle?*