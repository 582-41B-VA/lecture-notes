# Intro to Python

## Installation

You can download Python [here][download python]. Alternatively, you can
use the package manager of your choice (e.g. [Homebrew][] on Mac or
[Scoop][] on Windows). For further guidance, refer to the official
documentation:

-   [Using Python on Unix platforms](https://docs.python.org/3/using/unix.html)
-   [Using Python on Windows](https://docs.python.org/3/using/windows.html)

Once installed, make sure the Python interpreter has been correctly
added to your PATH. If so, executing the `python --version` command on
your terminal should print something similar to "Python 3.12.1".

Depending on your operating system and installation method, the Python
executable might be named `python3`. If this is the case, you can either
[create an alias][aliases] or substitute `python` for `python3`.

[download python]: https://www.python.org/downloads/
[Homebrew]: https://brew.sh
[Scoop]: https://scoop.sh
[aliases]: https://www.gnu.org/software/bash/manual/html_node/Aliases.html

## Documentation

The most accurate Python ressources are its [official documentation][]
and its [official tutorial][]. [Python Enhancement Proposals][], often
referred to as "PEP" followed by their number, are also a good source of
information. Of particular interest are [PEP 8 – Style Guide for Python
Code][PEP 8] and [PEP 20 – The Zen of Python][PEP 20].

The content for this introduction comes mostly from these ressources,
as well as from the [Composing Programs][] textbook by John DeNero, and
the book [Fluent Python][] by Luciano Ramalho.

[official documentation]: https://docs.python.org/3/
[official tutorial]: https://docs.python.org/3/tutorial/index.html
[Python Enhancement Proposals]: https://peps.python.org
[PEP 8]: https://peps.python.org/pep-0008/
[PEP 20]: https://peps.python.org/pep-0020/
[Composing Programs]: https://www.composingprograms.com
[Fluent Python]: https://www.oreilly.com/library/view/fluent-python-2nd/9781492056348/

## Executing scripts

To execute Python code saved in a file, simply pass the file's path as
an argument to the `python` command:

```sh
$ echo 'print("Hello World")' > tutorial.py
$ python tutorial.py
Hello World
```

## Interactive interpreter

Python comes with an interactive interpreter that operates somewhat like
the Unix shell. In an interactive session, you type some code after the
prompt, `>>>`. The Python interpreter then reads your code, executes it,
and prints the result.

To start an interactive session, execute the `python` command without
any arguments in your terminal.

In the following examples, input and output are distinguished by the
presence or absence of prompts (`>>>` and `…`). They should be omitted
when copying the code.

## Help built-in function

In an interactive session, the `help()` function will display the help
page for any object provided as an argument. For example, here is the
help page for the `print()` function used above in the "Executing
scripts" section:

```
print(*args, sep=' ', end='\n', file=None, flush=False)
    Prints the values to a stream, or to sys.stdout by default.

    sep
      string inserted between values, default a space.
    end
      string appended after the last value, default a newline.
    file
      a file-like object (stream); defaults to the current sys.stdout.
    flush
      whether to forcibly flush the stream.
```

## Indentation

Python syntax relies heavily on whitespace. It uses indentation ([PEP
8][] recommends 4 spaces) instead of curly braces to define blocks of
code structure. While code should always be properly formatted
regardless of the programming language, poorly indented Python code
simply will not execute.

## Basic data types

Python defines a number of built-in data types such as boolean, integer,
float, string, and so forth. We need not declare these types explicitly;
they are inferred (i.e. guessed) by the interpreter based on their
value.

We can use the built-in fonction `type()` to get the data type of a
given value:

```python
>>> type(10)
<class 'int'>
>>> type(True)
<class 'bool'>
>>> type("Hello")
<class 'str'>
```

### Integer and float numbers

Integer and Float numbers can be used to perform arithmetic with the
operators `+`, `-`, `*` and `/`. Parentheses can be used for grouping.
For example:

```python
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5
1.6
```

### Strings

Strings are immutable sequences of characters enclosed in single or
double quotes. They can be concatenated (glued together) with the `+`
operator, and indexed with square bracket notation:

```python
>>> "Py" + 'thon'
'Python'
>>> "Python"[3]
'h'
```

The built-in function `len()` returns the length of a string:

```python
>>> len('supercalifragilisticexpialidocious')
34
```

F-strings provide a way to embed expressions inside string literals. An
f-string is a literal string, prefixed with "f", which contains
expressions inside braces. The expressions are replaced with their
values at run time.

```python
>>> name = "Katniss"
>>> age = 16
>>> f"My name is {name}, and my age is {age}"
'My name is Katniss, and my age is 16'
```

## Compound data types

Python also defines compound data types used to group together other
values.


### Lists

Lists are mutable sequences of ordered items. They are written as a list
of comma-separated values between square brackets. Lists can contain
items of different types. For instance:

```python
>>> [1, 2, 3]
[1, 2, 3]
>>> [1, "b", ["c"]]
[1, 'b', ['c']]
```

Lists can be indexed and sliced. Slice operations return a new list
containing the requested elements:

```python
>>> [1, 2, 3][0]
1
>>> [1, 2, 3][1:]
[2, 3]
>>> [1, 2, 3][0:2]
[1, 2]

```

Lists support operations like concatenation, and unlike strings, which
are immutable, it is possible to change their content:

```python
>>> [1, 2] + [3, 4]
[1, 2, 3, 4]
>>> n = [1, 2, 3]
>>> n[-1] = 4
>>> n
[1, 2, 4]
```

You can also add new items at the end of the list by using the
`append()` method:

```python
>>> n = [1, 2, 3]
>>> n.append(4)
>>> n
[1, 2, 3, 4]
```

### Dictionaries

A dictionary is a set of "key: value" pairs, with the requirement that
the keys are unique within one dictionary. Square bracket notation can
be used to extract, mutate and add values. For example:

```python
>>> tel = {"jack": 4098, "sape": 4139}
>>> tel["jack"]
4098
>>> tel["sape"] = 4140
>>> tel["guido"] = 4127
>>> tel
{'jack': 4098, 'sape': 4140, 'guido': 4127}
```


When looping through dictionaries, the key and corresponding value can
be retrieved at the same time using the `items()` method:

```python
>>> for k, v in tel.items():
...     print(k, v)
...
jack 4098
sape 4140
guido 4127
```

### Tuples

A tuple is a list of values separated by commas, often enclosed in
parentheses. Contrary to lists, tuples are immutable; they cannot be
changed.

Tuples can be used as records where the meaning of each field is given
by its position in the tuple:

```python
>>> coordinates = (33.9425, -118.408056)
>>> rgb = (255, 54, 120)
```

Grouping values in a tuple is called *packing*. Values of any sequence
can also be *unpacked*:

```python
>>> latitude, longitude = coordinates
>>> longitude
-118.408056
>>> red, green, blue = rgb
>>> red
255
```

Sequence unpacking requires that there are as many variables on the left
side of the equals sign as there are elements in the sequence.

## Variables

Variables are bound to values using the equal sign. In Python, it is
better to think of variables as labels with names attached to objects,
rather than boxes where you store data. For example:

```python
>>> a = [1, 2, 3]
>>> b = a
>>> a.append(4)
>>> b
[1, 2, 3, 4]
```

Above, variables `a` and `b` hold *references* to the same list, not
*copies* of the list. Therefore, the `b = a` statement does not copy the
contents of box `a` into box `b`. It attaches the label `b` to the
object that already has the label `a`.

## If statements

Perhaps the most well-known statement type is the `if` statement. For
example:

```python
>>> resp = input("Please enter an integer: ")
Please enter an integer: 42
>>> resp = int(resp)
42
>>> if resp < 0:
...     print("Negative")
... elif resp == 0:
...     print("Zero")
... else:
...     print("Positive")
...
Positive
```

There can be zero or more `elif` parts, and the `else` part is optional.
The keyword `elif` is short for "else if".

## For loops

The `for` statement can be used to iterate over the items of any
sequence in the order that they appear in:

```python
>>> words = ["cat", "window", "defenestrate"]
>>> for w in words:
...     print(w)
...
cat
window
defenestrate
```

If you need to access the index while iterating, use the built-in
function `enumerate()`:

```python
>>> for i, w in enumerate(words):
...     print(i, w)
...
0 cat
1 window
2 defenestrate
```

## Functions

The keyword `def` introduces a function definition. It must be followed
by the function name and the parenthesized list of its parameters.
The statements that form the body of the function start at the next
line, and must be indented:

```python
>>> def plus(a, b):
...     return a + b
...
>>> plus(2, 2)
4
```

Default values can be specified. They allow functions to be called with
fewer arguments than the total number of parameters:

```python
>>> def greet(name, greeting="Hello"):
...     return f"{greeting} {name}"
...
>>> greet("Alice")
'Hello Alice'
>>>
```

Functions can also be called with keyword arguments:

```python
>>> greet(name="Yoko", greeting="Hi")
'Hi Yoko'
```

Functions can be *variadic*; i.e., they can accept a variable number of
arguments. Arguments are grouped together within the function's body as
a tuple.

```python
>>> def create_team(*members):
...     return members
...
>>> create_team("Naruto", "Sasuke", "Sakura")
('Naruto', 'Sasuke', 'Sakura')
```

## Classes

Classes provide a means of bundling data and functionality together.
Creating a new class creates a new type of object, allowing new
instances of that type to be made.

The `class` keyword is used to define a new class. A class statement
defines the class name, then includes statements that define the
*attributes* of the class:

```python
>>> class Animal:
...     count = 0
...
...     def __init__(self, name, kind):
...         self.name = name
...         self.kind = kind
...         Animal.count = Animal.count + 1
...
...     def greet(self):
...         return f"I am {self.name} the {self.kind}."
```

New instances can then be created by calling the class:

```python
>>> tony = Animal("Tony", "turle")
```

### Class variables

Data attributes assigned to classes, such as `count`, are called *class
variables*. They are *shared* by all instances of the class. They can be
accessed either from an instance or from the class object itself using
the dot notation:

```python
>>> tony.count
1
>>> sylvie = Animal("Sylvie", "rabbit")
>>> tony.count
2
>>> sylvie.count
2
>>> Animal.count
2
```

### Methods

Callable attributes, such as `__init__` and `greet`, are called
*methods*. They are usually called from instance objects using the dot
notation. The first argument of most methods, conventionally called
`self`, is bound to the instance object the method is called from.

```python
>>> tony.greet()
I am Tony the turtle.
```

### Constructor

The `__init__` attribute is a special method known as a *constructor*.
It is automatically called at instantiation to create a new object.
Within the constructor, statements can be included to initialize the
default state of the objects.

### Instance variables

Data attributes bound to `self` using the dot notation (such as `self.name`
and `self.kind`) are called *instance variables*. They are unique to
each instance, and can only be accessed from instance objects:

```python
>>> tony.kind
'turtle'
>>> sylvie.kind
'rabbit'
>>> Animal.kind
AttributeError: type object 'Animal' has no attribute 'kind'
```

### Inheritance

Classes can inherit attributes from other classes. The syntax for a
derived class definition looks like this:

```python
>>> class Dog(Animal):
...     def __init__(self, name):
...         super().__init__(name, "dog")
```

The `super()` function allows us to refer to the parent class
explicitly.

```python
>>> tobby = Dog("Tobby")
>>> tobby.greet()
I am Tobby the dog.
>>> Animal.count
3
```

## Lambdas

Small anonymous functions can be created with the `lambda` keyword.
Lambda functions can be used wherever function objects are required.
They are syntactically restricted to a single expression.

```python
>>> def make_incrementor(incr):
...     return lambda x: x + incr
...
>>> increment_by_2 = make_incrementor(2)
>>> increment_by_2(4)
6
```

## Exceptions

Errors detected during execution are called *exceptions*. They can be
handled with the `try` statement. If an exception occurs during
execution of the `try` clause, the rest of the clause is skipped. Then,
if its type matches the exception named after the except keyword, the
except clause is executed.

```python
>>> try:
...     i = input("Please enter a number: ")
...     int(i)
... except ValueError:
...     print(f"Oops! '{i}' is not a valid number.")
...
Please enter a number: apple
Oops! 'apple' is not a valid number.
```

## Decorators

Decorators are functions that wrap other functions. They are used to
transform a function without changing its body directly:

```python
>>> def exclaim(f):
...     def decorate():
...         return f() + "!"
...
...     return decorate
```

A decorator takes the function to be decorated (`f`) as an argument, and
returns the function to be called (`decorate`) when the decorated
function is called.

To decorate a function, add the decorator's name with the `@` symbol
above its definition:

```python
>>> @exclaim
>>> def greet():
...     return "Hi"
```

When called, the function will be automatically decorated. Thus,
`greet()` is equivalent to `exclaim(greet)()`.

```python
>>> greet()
Hi!
```

The function returned by a decorator (`decorate`) can access the
arguments of the decorated function (`a` and `b`):

```python
>>> def print_args(f):
...     def decorate(a, b):
...         print("Arguments:", a, b)
...         print("Result:", f(a, b))
...
...     return decorate
...
>>> @print_args
>>> def add(a, b):
...     return a + b
...
>>> add(1, 2)
Arguments: 1 2
Result: 3
```

Decorators can also accept their own arguments, in which case they need
to be wrapped in another function:

```python
>>> def repeat(n):
...     def decorator(f):
...         def decorate():
...             for _ in range(n):
...                 f()
...
...         return decorate
...
...     return decorator
...
>>> @repeat(3)
>>> def sing():
...     print("La la la")
...
>>> sing()
La la la
La la la
La la la
```

## Modules

As your program gets longer, you may want to split it into several
*modules* for easier maintenance. A module is a file that contains
Python executable statements as well as function definitions. Each
module has its own private namespace, which is used as the global
namespace by all functions defined in the module.

Modules can import other modules. For instance, suppose you have a
Python file named "fibo.py" in a project directory:

```python
# fibo.py

def fib(n):
    result = []
    a, b = 0, 1
    while a < n:
        result.append(a)
        a, b = b, a + b
    return result
```

You can import the `fibo` module into another module from the same
directory using the `import` keyword. It is customary to place all
import statements at the beginning of a module. The imported module
name, which corresponds to its filename without the ".py" extensions, is
added to the current module's global namespace:

```python
# app.py

import fibo

fibo.fib()
```

It is possible to import names from a module directly into the importing
module's namespace using the `from` keyword. It can, however, make the
code more difficult to understand.

```python
# app.py

from fibo import fib

fib()
```

## Standard library

Python comes with a library of standard modules, documented
[here][stdlib]. Python's standard library is very extensive, offering a
wide range of facilities. The library contains built-in modules that
provide access to system functionality such as file I/O that would
otherwise be inaccessible to Python programmers, as well as modules
written in Python that provide standardized solutions for many problems
that occur in everyday programming.

[stdlib]: https://docs.python.org/3/library/index.html

The `datetime` module, for instance, supplies classes for manipulating
dates and times. It is imported in the current module's namespace using
the `import` keyword, and can be used like any other modules:

```python
>>> import datetime
>>>
>>> d = datetime.date.fromisoformat("2017-06-01")
>>> d.strftime("%B %d, %Y")
June 01, 2017
```