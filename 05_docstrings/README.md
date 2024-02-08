# Style guide for docstrings

A docstring is a string literal surrounded by triple double quotes that
occurs as the first statement in a module, function, class, or method
definition. Such a docstring becomes the `__doc__` special attribute of
that object, which is used by various tools to produce documentation.

This document explains how to properly use docstrings for this course.
It mostly follows [PEP 257][] and [Google's Python style guide][].

[PEP 257]: https://peps.python.org/pep-0257/
[Google's Python style guide]: https://google.github.io/styleguide/pyguide.html

## Module

Files should start with a docstring describing the contents and usage of
the module. Module docstrings should adhere to the following format:

```python
"""A one-line summary of the module or program, terminated by a period.

Leave one blank line. The rest of this docstring should contain an
overall description of the module or program.
"""
```

## Classes

Classes should have a docstring below the class definition describing
the class. It should start with a one-line summary that describes what
the class instance represents.

```python
class CheeseShopAddress:
    """The address of a cheese shop.

    Further description, if necessary.
    """
```

## Functions and methods

A docstring is mandatory for every function. It should give enough
information to write a call to the function without reading the
function's code. It should describes its use, but not how it is
implemented (unless its implementation is relevant).

Certain aspects of a function should be documented in special sections,
listed below. Each section begins with a heading line, which ends with a
colon. All sections other than the heading should maintain a hanging
indent of four spaces.

```python
def function(a, b):
    """A one-line summary of what the function does.

    Further explanation, if necessary.

    Args:
        a (str): Brief description of the argument.
        b (int): Longer description that includes a lot of bla bla bla bla bla
            bla bla bla bla bla bla bla.

    Returns:
        A string that contains bla bla bla.
    """"
```