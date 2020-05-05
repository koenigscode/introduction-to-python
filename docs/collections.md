# Collections

## List

A list is an ordered collection, allows duplicate members and is changeable.

### Creation

```python
l = []
l = [1,2,3]
l = list()
l = list(iterable)
```

You can create a new list using either two square brackets or the list constructor.
If you want to create a list from an iterable, you need to use the
`list()` constructor:

```python
r = range(1, 10)  # creates a new range object
print(f"range: {r}")  # r is a range object, not a list

try:
    r.add(11)
except AttributeError as e:
    # as r is a range object rather than a list,
    # you can't add an item to it
    print(f"error: {e}")

# as range instances are iterable,
# you can create a normal list from them:
l = list(r)
print(f"list: {l}")
```

```
range: range(1, 10)
error: 'range' object has no attribute 'add'
list: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### Append Item

```python
l.append(item)
```

### Set Item At Index

```python
l[index] = item
```

### Insert Item At Index

```python
l.insert(index, item)
```

### Extend List

```python
l.extend(iterable)
```

`l.append([1,2,3])` would add a list containing three items to our list.
So when we want the items of an iterable (e.g. list) to be added item for item to our list, we can instead extend our list with that iterable.

```python
l1 = [1, 2, 3]
l1.append([4, 5, 6])

l2 = [1, 2, 3]
l2.extend([4, 5, 6])

print(l1)
print(l2)
```

```
[1, 2, 3, [4, 5, 6]]
[1, 2, 3, 4, 5, 6]
```

### Access Item

```python
item = l[index]
```

see [List Slicing](#list-slicing) for advanced syntax

### List Length

```python
len(l)
```

### Occurrences Of Item

```python
l.count(item)
```

### Index Of Item

```python
l.index(item)
```

### Change Item Value

```python
l[3] = "new value"
```

### Remove Item By Value

```python
l.remove(item)
```

Removes the item if it is present, otherwise raises KeyError.

### Remove Item By Index:

#### Pop

```python
l.pop()
l.pop(index)
```

Removes the item at the specified position; if no index is given, it removes the last item in the list. Returns the removed value.

#### Delete Statement

```python
del l[index]
```

When using the `del` statement the removed value will not be
returned.

### Membership Testing

```python
item in l
item not in l
```

### Reverse List

```python
l.reverse()
```

### Sort List (In Place):

```python
l.sort()
l.sort(key=my_comparison_function, reverse=my_boolean)
```

Sorts the list in place (i.e. changes the original list instead of returning a new one). `key` is an optional function used to compare the elements to each other.

### Sort List (As Copy)

```python
l = sorted(iterable)
sorted(iterable, key=my_comparison_function, reverse=my_boolean)
```

Returns a new, sorted list. Keeps the original iterable unchanged.

### Clear List

```python
l.clear()
```

Using the `l.append()` and `l.pop()` methods, lists can be used as stacks

### List Slicing

TODO

## Set

A set is an unordered (therefore unindexed) and changeable collection without duplicate
items.

### Creation

```python
s = set()
s = set(iterable)
```

You **cannot** create a set using two empty curly braces \textit{\{ \}} as this would
create an empty dictionary.

### Add Item

```python
s.add(item)
```

If the element is already in the list, it won't be added again.

### Update (Extend) Set

```python
s.update(iterable)
```

Adds all elements from `iterable` to the set.

### Remove Item

```python
s.remove(item)
```

Removes the item if it is present, otherwise raises a `KeyError`.

### Discard Item

```python
s.discard(item)
```

Removes the element if it is present, otherwise does nothing.

### Membership Testing, Length, Clear:

Same as the [List](#list) functions

## Dictionary

A dictionary **(map, associative array)** is a mapping of key-value pairs.

### Creation

```python
d = {}
d = {key: val}
d = dict()
d = dict(iterable)
```

You can create a dictionary from an iterable containing indexable items (e.g. lists) with a length of 2:

```python
iterable = [[1, "one"], [2, "two"], [3, "three"]]
print(dict(iterable))
```

```
{1: 'one', 2: 'two', 3: 'three'}
```

### Add/Set Key-Value Pair

```python
d[key] = val
```

### Update (Extend) Dictionary

```python
d.update(dictionary)
d.update(iterable)
```

Adds all key-value pairs from the given dictionary to the dictionary `d`.
You can also extend the dictionary with an iterable containing indexable items (e.g. lists).

### Access Value

```python
val = d[key]
```

Raises a `KeyError` if the dictionary does not contain the key.

### Get Method

```python
val = d.get(key)
val = d.get(key, default=my_fallback_value)
```

Returns the default value if the dictionary does not contain the key.
The default value's default value is None.

### Remove Item

#### Pop

```python
d.pop(key)
```

Removes the key-value pair at the given key. Returns the removed value.

#### Delete Statement

```python
del d[index]
```

When using the `del` statement the removed value will not be
returned.

### Dictionary Keys

```python
d.keys()
```

Returns all the keys of a dictionary as a `dict_keys` object. If you would like a normal list instead, just call the list constructor and pass
the dict_keys object along as you would do with any iterable:
`list(d.keys())`.

### Dictionary Values

```python
d.values()
```

Returns a dict_values object. Use `list(d.values())` to get a list instead.

### Get Key-Value Pairs As List Of Tuples

```python
d.entries()
```

Returns an iterable with tuples containing the key and value.

Is especially useful for iterating dictionaries:

```python
d = {1: "one", 2: "two", 3: "three"}
print(d.items())

for key, val in d.items():
    print(f"{key}: {val}")
```

```
dict_items([(1, 'one'), (2, 'two'), (3, 'three')])
1: one
2: two
3: three
```

### Membership Testing

#### Check For Key

```python
key in d
```

#### Check For Value

```python
key in d.values()
```

### Length, Clear

Same as the [List](#list) functions

## Tuple

Tuples are collections that can, once created, not be changed, meaning you
cannot add or remove items.

### Creation

```python
t = ()
tuple()
t = item1, item2}
t = (item1, item2)
t = tuple(iterable)
```

You can create tuples containing any amount of items; as you cannot add elements to an existing tuple, you will not need to create an empty one very often.

### Access Item, Index Of Item, Occurrences Of Item, Membership Testing, Length

Same as the [List](#list) functions

Items cannot be added or removed; if an item within the tuple is mutable, however, the item itself may be changed.

As you can see, a tuple's functionality is quite limited compared to lists.
So why would you use them? Well, for once they are faster than lists and
**they enable to you to "return multiple values from a function" thanks to unpacking**

### Tuple Unpacking

If you got a tuple consiting of **n** elements, you can **unpack** it and save its individual items in **n** (and **exactly** **n**) variables.

```python
t = 5, 3, -1
x, y, z = t
print(f"x: {x}, y: {y}, z: {z}")
```

```
x: 5, y: 3, z: -1
```

If you try to unpack a tuple containing **n** elements to less or more than **n** variables, an error will be raised. Items not needed are often saved to a dummy variable `_`.

```python
t = 5, 3, -1

try:
    x, y = t
except ValueError as e:
    print(e)

try:
    x, y, z, w = t
except ValueError as e:
    print(e)

x, y, _ = t
print(f"x: {x}, y: {y}")
```

```
too many values to unpack (expected 2)
not enough values to unpack (expected 4, got 3)
x: 5, y: 3
```

## Iterating
TODO
