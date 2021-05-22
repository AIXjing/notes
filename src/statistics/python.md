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

## 2.1 Basic concepts

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

## 2.2 Basic sets

### 2.2.1 Sets within Sets

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

### 2.2.2 Visualization

* Venn Diagram

```py
import matplotlib.pyplot as plt
import matplotlib_venn as venn
S = {1, 2, 3}
T = {0, 2, -1, 5}
venn.venn2([S, T], set_labels=('S','T'))
plt.show()

#for 3 sets: venn.venn3([S,T,U], set_labels=(’S’,’T’,'U'))
```

## 2.3 Relations

### 2.3.1 Number relations

* Equality

  \\(=\\), \\(\neq \\)

* Intersection - two sets share at least one common element

  Disjoint - no shared elements

* Subsets - \\(A \subseteq B\\) 

  superset - \\(B \supseteq A\\) 

  \\[
    P \subseteq N \subseteq Z \subseteq Q \subseteq R
  \\]

  strict subset - if \\(A \subseteq B\\) and \\(A \neq B\\), A is a strict subset of B, denote \\(A \subset B\\); conversely, A is a strict superset of B, \\(B \supset A\\)

**Belongs to (\\( \in \\)) vs. Subsets of (\\(\subseteq \\))**

- \\( x \in A \\): element x belongsto set A

  \\( 0 \in {0,1} \\)

- (\\( A \subseteq B \\)): A is a subset of B

   \\( \\\{ 0 \\\} \subseteq {0,1} \\)

*Python to check equality and disjoint*

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

*Python to check subsets and supersets*

`<=` or `issubset` for \\(\subseteq \\) and `<` for \\(\subset \\) 

`>=` or `issuperset` for \(\supseteq \\) 

```py
zero = {0}; zplus = {0,1}; zminus = {0, -1}

ziminus <= zplu
#Output: False
ziminus >= zplu
#Output: True

zero.issubset(zminus)

```