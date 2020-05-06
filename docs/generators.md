# Generators
Your memory probably can't handle a list of hundreds of thousands of elements.
Therefore we use generators for tasks like this instead.
Generators calculate and deliver a value when it's needed.

Consider the following example:

```python
def primes_generator():
    yield 2  # yield two

    number = 3  # then start with 3
    while True:
        for div in range(2, number):
            if number % div == 0:
                number += 1
            else:
                yield number  # yield the prime number
                number += 1


# get an instance of the generator
primes = primes_generator()
print(f"primes object: {primes}")

# print first 10 primes
for i in range(10):
    print(next(primes))
```

```
primes object: <generator object primes_generator at 0x000001B72D371FC0>
2
3
5
7
9
11
13
14
15
17
```

At first, we define a new generator.
Functions only return one value, generators, on the other hand, can
**yield** multiple values.

Upon calling `gen()` on line 14 we get a generator object, so an instance
of the generator function

When we call `next(g)` (with g being the generator object) the generator
function executes till it reaches the next `yield` statement.

Once a value is being yielded, the generator function stops and returns
the yielded value.

At the next `next(g)` the generator function resumes till it reaches
its next `yield`.
