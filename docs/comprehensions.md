# Comprehensions

Often you want to create basic collections following a simple pattern, let's say a list
containing all the squares of the numbers 1 to 10. You had to create an empty list and then
fill it within a for loop.

To do this with less code, Python provides different kinds of comprehensions to create
collections in one line.

The list comprehension will probably be your most used one:

## List Comprehensions

Let's take the example I just talked about and code it with the knowledge we acquired so far:

```python
l = list()  # create list
for x in range(1, 11):  # range from 1 to 10
    l.append(x**2)  # square x and add to list
print(l)
```

```
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

To achieve the same with a list comprehension:

```python
l = [x**2 for x in range(1, 11)]
print(l)
```

```
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

The **first expression** - in this case `x**2` -
is **added to the list** and this is repeated for every `x` in
`range(1,11)`, so the numbers 1-10 (as the end of the range -
the second parameter - is exclusive).

You can also use nested for loops:
`l = [x for x in item for item in list]`

### Filtering Elements

If you only want to add an element to the list if a certain criterion is met, you can add an `if` statement **at the end of the comprehension**:

```python
l = [x**2 for x in range(1, 11) if x % 2 == 0]
print(l)
```

```
[4, 16, 36, 64, 100]
```

### Ternary Operator

You can use the ternary operator in the first expression of the comprehension to decide which value to add to the list based on some condition.

Note that the ternary operator - the **if at the start of the comprehension** - decides on which value to add to the list and the if at the end of the comprehension decides on whether the element should even be added to the list or not.

```python
# if the character is not a blank, add it to the list
# if it already is an uppercase character, leave it that way,
# otherwise make it one
l = [c if c.isupper() else c.upper()
     for c in "This is some Text" if not c == " "]
print(l)
# join the  list and put "" (nothing) between each item
print("".join(l))
```

```
['T', 'H', 'I', 'S', 'I', 'S', 'S', 'O', 'M', 'E', 'T', 'E', 'X', 'T']
THISISSOMETEXT
```

As you can see, the comprehension got quite long and therefore I decided to put a line break in.

If your comprehension gets complex you should definitely consider using a normal loop instead}, as it's probably easier to read.

## Set Comprehensions

Set comprehension work just like list comprehension with the difference that they return a set instead (so duplicates are filtered out) and are created using two curly braces: `s = {item for item in iterable}`

## Dictionary Comprehensions

Dictionary comprehensions use curly braces, however, their first expression is a key-value pair:

```python
letters = ["A", "B", "C", "D", "E"]
d = {key: val for key, val in enumerate(letters, 1)}
print(d)
```

```
{1: 'A', 2: 'B', 3: 'C', 4: 'D', 5: 'E'}
```

## Generator Comprehensions

Generator comprehensions use parentheses and create an instance of a generator:

```python
g = (x for x in range(1024))

for i in range(5):
    print(next(g))
```

```
0
1
2
3
4
```
