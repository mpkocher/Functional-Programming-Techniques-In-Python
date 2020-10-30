# Functional Programming Techniques In Python

<p align="center">
<img src="https://raw.githubusercontent.com/mpkocher/Functional-Programming-Techniques-In-Python/main/logo.png" />
</p>

```python
import functools

def compose(*funcs):
    """Functional composition [f, g, h] will be h(g(f(x))) """
    def compose_two(f, g):
        def c(x):
            return f(g(x))
        return c
    return functools.reduce(compose_two, reversed(funcs))


def adder(a: int, b: int) -> int:
    return a + b


def multiply(n: int):
    def wrapper(m: int) -> int:
        return m * n
    return wrapper

add_one = functools.partial(adder, 1)
add_two = functools.partial(adder, 2)


f = compose(add_one, multiply(3), add_two)
assert f(7) == 26

fp = compose(f, print)
fp(7)
```

## Exploring functional centric design style and patterns in Python


This is a 4 Part Series that explores functional centric design style and patterns in Python.


[Part 1 (notebook)](https://github.com/mpkocher/Functional-Programming-Techniques-In-Python/blob/main/Functional-Python-Part-1.ipynb) starts with different mechanisms of how to define functions in Python and quickly moves to using [closures](https://en.wikipedia.org/wiki/Closure_(computer_programming)) and `functools.partial`. We then move on to adding `functools.reduce` and  composition with [compose](https://gist.github.com/mpkocher/9896022) to our toolbox. Finally, we conclude with adding lazy `map` and `filter` to our toolbox and create a data pipeline that takes a stream of records to compute common statics using a max heap as the reducer. 

In [Part 2 (notebook)](https://github.com/mpkocher/Functional-Programming-Techniques-In-Python/blob/main/Functional-Python-Part-2.ipynb), we explore building a REST client using functional-centric design style. Using an iterative approach, we build up a REST client using small functions leveraging clsoures and passing functions as first class citizens to methods. To conclude, we wrap the API and expose the REST client via a simple Python class.

[Part 3 (notebook)](https://github.com/mpkocher/Functional-Programming-Techniques-In-Python/blob/main/Functional-Python-Part-3.ipynb) follows similarly to spirit to Part 2. We build a commandline interface leveraging `argparse` from the Python standard library. Sometimes libraries such as argparse can have rough edges or friction points in the API that introduce duplication or design issues. Part 3 focuses on iterative building up an expressive commandline interface to a subparser commandline tool using closures and functions to smooth out the rough edges of `argparse.`. There's also examples of using a Strategy-ish pattern with type annotated functions to enable configuring logging as well as custom error handling. 

[Part 4 (notebook)](https://github.com/mpkocher/Functional-Programming-Techniques-In-Python/blob/main/Functional-Python-Part-4.ipynb) concludes with some gotchas with regards to scope in closures, a brief example of decorators and a few suggestions for leveraging function-centric designs in your APIs or applications. 

If you're a OO wizard, a Data Scientist/Analysist, or a backend dev, this series can be useful to expand your skillset and provide you with a new design approach to building APIs or applications.

[Originally posted here](https://mpkocher.github.io/2019/03/01/Functional-Programming-Techniques-In-Python-Series/)


## Other Resources

- https://github.com/pytoolz/toolz
- https://github.com/dry-python/returns
- https://github.com/getify/Functional-Light-JS
- https://github.com/sfermigier/awesome-functional-python

