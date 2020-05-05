# Functions

I assume you already know about functions; this is what their basic syntax looks like in Python:

```python
def my_function(x, y):
    return x+y

print(my_function(2, 3))
```

```
5
```

## Default Parameters

You can also set default parameters by saying
`def my_function(x=1, y=1):`
so you can call the function with zero, one or two arguments.
Parameters with a default value are **optional arguments**, those without are called **positional arguments**.

Note that **optional parameters** must be the last arguments in the function definition.
So `def my_function(x=1, y):` is not a valid definition.

## Specifying Data Types

```python
def my_function(x: int, y: int) -> int:
```

However, everyone's still able to pass variables of any kind to that function,
meaning **the data type is not enforced** by any means but just
for documentation and readability!

```python
# receives two ints, returns a list
def quotient_and_remainder(divisor: int = 1, dividend: int = 1) -> []:
    return [divisor/dividend, divisor % dividend]


print(quotient_and_remainder(5, 3))
print(quotient_and_remainder(7))
print(quotient_and_remainder())
print(quotient_and_remainder(divisor=7))
```

```
[1.6666666666666667, 2]
[7.0, 0]
[1.0, 0]
[7.0, 0]
```

If you wanted to return two items you'd usually return a tuple instead of a list like I did, so we'll revisit this function later and improve it when we talk about tuple unpacking.

As you can see on line 9 you can **set a parameter by its variable name**
instead of position.

This is especially useful when working with functions which can have a huge number of optional
arguments and you need to only set some specific ones.

## Arbitrary Argument Lists

Sometimes you want to be able to call a function with any number of variables;
in Python, this is done with *args and you might know this concept from other programming
languages as __varargs__ (variables arguments).

Let's take a function `my_sum()` as an example:

```python
def my_sum(*args):
    sum = 0
    for number in args:
        sum += number

    return number


print(my_sum(1, 2, 3))
print(my_sum(1, 2, 3, 4, 5))
```

```
3
5
```

The function `my_sum()` stores all the values it gets in the *args list.
The * denotes that the variables called 'args' takes all the spare values; The * variable must be written after all the positional and optional arguments. `args`, not `*args`!

## Keyword Arguments
Arbitrary argument lists contain a list of spare values, keyword arguments, on the other hand,
are dictionaries containing spare values set in the function call with the
`key=value` syntax.

```python
def describe_object(item, **kwargs):
    print(f"item: {item}")
    # for x in kwargs would only return the dictionary's keys
    # the items function returns both the keys and values
    for key, value in kwargs.items():
        print(f"{key}: {value}")


describe_object(item="apple", size=5, cost=1, color="red")
```

```
item: apple
size: 5
cost: 1
color: red
```

Note that `item` is not a keyword argument, as `item` is a normal variable
from the function definition, however, its value can still be set using the `key=value` syntax in the function call.

## Lambdas
Lambdas are a shorthand for one-line functions and created using the
`lambda` keyword. They receive variables and their function body consists
of only one term, whose value also gets returned, therefore an explicit
`return` is not needed.

For typical use cases, see [Common Built-In Functions](common_built_in_functions)

```python
# The following lambda receives two parameters x and y
# and returns their sum
f = lambda x,y: x+y # lambda is stored in variable f

print(f(2,3)) # lambda stored in f gets called
```

```
5
```