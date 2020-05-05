# Modules

## Imports

Once you've installed a module (or it's part of the standard library) you can easily import it using the import statement.

Let's consider numpy as an example:

`import numpy` enables you to access numpy's objects and modules,
for instance, the `ones` method (which gives you an array filled with zeros)
by calling `numpy.ones((2,2))`.

### Alias

Most of the time, however, you'll see people use `np` as an alias for numpy.
Just type `import numpy as np` and you're able to call the
`ones` method with `np.ones((2,2))`

If you just need some specific objects or methods, like the `zeros` or `ones`
method,
you can import them by using `from numpy import zeros, ones`.
You can then access the methods by simply saying
`ones((2,2))` and there's no need for the 'numpy' at front.

### Import *

Newcomers often tend to use `from numpy import *` which
enables you to use any method or object from the module without prefixing
it with the module name at the front or importing it explicitly by using its name.

However, using `from x import *` should be avoided
as it pollutes your namespace, meaning you've got a problem if
two or more modules have members with the same name.

Consider the following example:
```python
"""content of module_a.py:
# some_var = 1
"""

"""content of module_b.py:
# some_var = 0
"""

from module_a import *  # better: import module_a as a
from module_b import *  # better: import module_b as b


print(some_var)
# better: print(a.some_var)
# better: print(b.some_var)
```

```
0
```

In both modules, a variable `some_var` was declared and set to different values.
As you can see in the output, `some_var` from b overwrote `some_var` from a.
To avoid these kind of issues, just import modules under a short alias, like np for numpy, pd for pandas or tk for tkinter.

All the methods introduced above also work for submodules, so to use the pyplot submodule from matplotlib as `plt` you can import it using
`import matplotlib.pylot as plt`.

## PIP

pip is one of the most used package managers for Python and if you've got Python 3.4 or later
it's already installed on your system.

Installing a new package/module is as simple as running
`pip install <package_name>`

You should then be able to import the newly installed package in Python using the
`import` statement.

As an example, let's install [scikit-learn](https://scikit-learn.org/), a library for machine learning, and import it:
```bash
$ pip install sklearn
```

```python
from sklearn.datasets import load_iris
iris = load_iris()  # load example dataset
data = iris.data  # get the data of the dataset
print(data[:3])  # print first three entries
```

```
[[5.1 3.5 1.4 0.2]
 [4.9 3.  1.4 0.2]
 [4.7 3.2 1.3 0.2]]
```