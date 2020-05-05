# Basic Syntax

## If/Else \& For In

```python
for i in range(10):
    if i % 2 == 0:
        print(i)
    elif False:
        # this condition is never reached
        pass  # pass does nothing
    else:
        print("odd number")
```

```
0
odd number
2
odd number
4
odd number
6
odd number
8
odd number
```

### Chaining Conditions

Python enables you to chain conditions:

```python
if 1 < 2 < 3:
    print('chaining conditions works!')
```

```
chaining conditions works!
```

### Ternary Operator (Inline If/Else)

The ternary operator works like in other languages, however, you're not using special
characters like `?` or `:` but the keywords `if` and `else`

```python
some_condition = True
x = 1 if some_condition else 0
print(x)
```

```
1
```

Note that, however, `x = 1 if some_condition` is not valid; you need an `else` statement.

## Reading From Command Line
You can get some input from the command line using the
`input` function:

```python
name = input("Enter your name: ")
print("Hello " + name + "!")
```

```
Enter your name: Michael
Hello Michael!
```

## Comments
Single line comments start with a `#`, docstrings ('multiline comments') comments start and end with `"""`.
However, you should use `#` for 'normal' comments and `"""` for docstrings (e.g. explaining the purpose of a class or function).

```python
# this is a single-line comment

"""
This is a
docstring/multi-line comment
"""

x = """
You can create a
multiline string using triple "
"""
```

## Data Types
Python basically has the following data types:
- Integer
- Float
- Complex Number
- String
- Boolean (`True` and `False` are capitalized)
- None (null in other languages)
- Function

You can negate booleans using the `not` statement: `not False == True`

It also features collections like sets and dictionaries by default, see [Collections](collections)

## Strings

### Creation
You can create a string using either single or double quotes;
it doesn't matter, which one you choose, just be consistent and
stick to one style.

### String Operations
```python
x = 'some string'
x = "some string"

x = """this is
a multiline string
"""

print("Hello " * 3)
print("Hello".upper())
print("Hello".lower())
print("Hello".count("l"))
print(ord("A"))  # get unicode position

for c in "Hello":  # iterate character by character
    pass  # pass does nothing
```

You can also use `"""` to create multiline strings

### String Formatting
Concatenating strings with numbers `"Python " + 101` results
in an error.

Gladly, there are some workarounds on how to format your strings:

#### F-Strings (preferred method)
```python
f"Python {101}"
```

#### Making everything a string}
```python
"Python" + str(101)
```

#### Modulo Operator
```python
"Python %s" % (101)
```

Calculating \texttt{string \% tuple} works because Python enables you to overwrite operators. This has nothing to do with an actual modulo operation, it's just used for simplicity. To learn more about operator overloading, take a look at [OOP](oop).

#### Format Method
```python
"Python {}".format(101)
```

Here are some examples:

```python
who = "I"
version = 3

print( who + " love Python " + str(version) )
print( "%s love Python %s" % (who, version) )
print( "{} love Python {}".format(who, version) )
print( f"{who} love Python {version}" )
```

```
I love Python 3
I love Python 3
I love Python 3
I love Python 3
```

### Raw String Literals
Raw String Literals, often called Raw Strings, are Strings in which `\`
is interpreted as the actual `\` character.

```python
s = r"\ is an actual backslash! \n"
print(s)
```

```
\ is an actual backslash! \n
```

## Parse Numbers
You can parse numbers from strings using the
`int` and `float` methods:

```python
print(int("3"))
print(float("3.14"))

# Raises an error:
int("hello")
```

```
3
3.14
Traceback (most recent call last):
  File "/home/michael/work/code/python-introduction/content/partials/basic_syntax/parse_numbers.py", line 5, in <module>
    int("hello")
ValueError: invalid literal for int() with base 10: 'hello'
```

## Special Operators
Python provides some special operators:

```python
x = 0
print( 3 ** 2 ) # 3 to the power of 2
print( 3 // 2 ) # integer division (floor of normal division)

x += 1 # increment x by one
# of couse also possible with -=, +=, /*, %=
print(x)
```

```
9
1
1
```

Note that there is no `x++` in Python; you need to use `x += 1`

## 'Main' In Python
You probably know the `main()` method from other languages such as Java or C.
Python, on the other hand, is primarily used for scripting, meaning there's a specific file
to be run rather than a single executable program.
By default, a Python file is executed from top to bottom, no matter whether this is the
'main' file (the file started e.g. from the command line by using
`python main.py`) or just a module imported by `main.py`

If you want some part of a program only executed if it's the 'main' file, so the
'entry point' to your program, you can check whether a certain variable called
`name` is equal to `"main"`:

```python
if __name__ == "__main__":
    # this part of the code will only be executed
    # if this is the 'entry' point of the program
    print("this is the main file")
```

```bash
$ python main.py
this is the main file
```

If you import this file from another file and execute the latter one, the code within the main of the imported file will not be executed.

## Exception Handling
You probably already know Error or Exception Handling from other object-oriented programming languages.

Generally, we differentiate between two types of errors: syntax errors and exceptions
Syntax errors can - and must be - avoided, exceptions, on the other hand, have different
origins.
For example, you might ask the user for a number - you get the user's input in the form of a string. You then try to parse the string - however, before trying to parse a number from it you don't know whether the user entered a valid number or not.

There's also a `finally` statement in Python which is used for clean-up
actions like closing files. It's always executed, even when an exception occurred or you
used a break, continue or return statement.

```python
try:
    print("text " + 3)
except TypeError as e:
    print(e)
finally:
    print("This will always be printed out")
```

```
must be str, not int
```

If you want to raise (in other languages 'throw') an error, use the raise keyword:
```python
raise ValueError("This a ValueError")
```

```
Traceback (most recent call last):
  File "d:/work/code/python-introduction/content/partials/basic_syntax/raise_error.py", line 1, in <module>
    raise ValueError("This a ValueError")
ValueError: This a ValueError
```

There's also a finally clause which will always be executed (unless you exit or kill
the program).

```python
f = open("file.txt", "w")

try:
    # use file
except EOFError:
    # handle error appropriately
finally:
    # if the file is not closed yet, do so
    if not f.closed():
        f.close()

```

In this example the `with` context manager is probably a better option,
as he automatically closes opened files; see [Working with Files](working_with_files)
