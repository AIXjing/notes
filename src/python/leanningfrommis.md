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

## Virtualenv - virtual environment manager

`venv` for Python 3 or `virtualen` for Python 2

[Installing packages using pip and virtual environments](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment)

[Installing venv](https://docs.python.org/3/library/venv.html#module-venv)

### This is how I did for my "Energy-data" project:

Copy the following code into "init_py.sh" file

```
#!/bin/bash
set -e

PYTHON_ENV_NAME=venv

pip3 install virtualenv

# or 'sudo pip3 install virtualenv'

virtualenv -p python3 $PYTHON_ENV_NAME

echo "source $(pwd)/$PYTHON_ENV_NAME/bin/activate" > .env

source $(pwd)/$PYTHON_ENV_NAME/bin/activate # activate the local python environment

pip3 install jupyter
pip3 install matplotlib
pip3 install pandas
pip3 install scipy
pip3 install seaborn
pip3 install graphviz
pip3 install scikit-learn

echo -e "\n"
echo "Please run \"$ source $PYTHON_ENV_NAME/bin/activate\" to switch to the python environment."
echo "Use \"$ deactivate\" anytime to deactivate the local python environment if you want to switch back to your default python."
echo "Or install autoenv as described on project readme file to make your life much easier."
```

### Other easy ways to do

[Video source from Corey Schafer](https://www.youtube.com/watch?v=N5vscPTWKOk)

[Text insruction](https://www.pythonforbeginners.com/basics/how-to-use-python-virtualenv)
