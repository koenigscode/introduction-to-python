# Advanced
There are several advanced or rarely used statements or concepts in Python.
Some of them will be featured in the following sections:

## Assert
The assert statement is used to debug applications.
You can assume a condition is `True` and if it isn't,
an `AssertError` will be thrown.


```python
x = 1
assert x == 1
assert x == 0
```

```
Traceback (most recent call last):
  File "/home/michael/work/code/python-introduction/content/partials/advanced/assert_example.py", line 3, in <module>
    assert x == 0
AssertionError
```

## Else

In Python you can use `else` along other statements beside
`if`

### For & While
An else statement after a `for` or `while` will be executed if the loop finished normally, meaning no `break`
occurred.

### Try-Except
An else statement after a try-except will be executed if no error occurred within the try block.

## Regular Expressions

## Decorators
