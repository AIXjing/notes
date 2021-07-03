# Learning in a hard way

## numpy.array

When creates a numpy.array `a = numpy.array([1,2,3])`. It is 1-dimensional if not specified. The shape of a can be checked out by `a.shape`, and it will output `(3,)`.

The number of dimensions will be transformed from 1 to 2 by exploting 

- `a1 = a.reshape(1,3)`, giving an output `array([[1,2,3]])`

- `a2 = a.reshape(3,1)`, giving an output 

```py
array([[1],
       [2],
       [3]])
```

**array.sum**

- array.sum(axis=0): sum up along the column

```py
a1.sum(axis=0)
#output: array([1, 2, 3])

a2.sum(axis=0)
#output: array([6])
```

- array.sum(axis=1): sum up along the row

```py
a1.sum(axis=1)
#output: array([6])

a2.sum(axis=1)
#output: array([1, 2, 3]) -> 1D array?
```

`a.sum(axis=1)` and `a.sum(axis=0)` give the same output `array([6])` because of only one dimension.

![image](https://user-images.githubusercontent.com/41487483/119228773-d0b20600-bb14-11eb-9fa9-93e697500f1c.png)


## Easy coding

1. ´x = x + 1´ is qual to ´x += 1´