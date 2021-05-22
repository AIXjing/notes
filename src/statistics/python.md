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

