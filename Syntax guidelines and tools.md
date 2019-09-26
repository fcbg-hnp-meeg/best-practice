
# <center> Python syntax guidelines and tools </center>

This document aims to describes some of the main guidelines to code your python scripts. These are directly extracted from PEP 8 documentation and only cover most used cased. To get full PEP 8 recommandations, please use the following link.

https://www.python.org/dev/peps/pep-0008/

Some tools designed to facilitate respect these guidelines are presented at the end of the document.

## <center> Guidelines </center>

### Source File Encoding

Code in the core Python distribution should always use UTF-8.


### Indentation

Use 4 spaces per indentation level.
Spaces are the preferred indentation method.

Tabs should be used solely to remain consistent with code that is already indented with tabs.

### Imports

Imports should usually be on separate lines:


```python
#Yes
import os
import sys
```


```python
#No
import sys, os
```

but it's ok to do:


```python
from numpy import mean, std
```

Imports should be grouped in the following order:

    1. Standard library imports.
    2. Related third party imports.
    3. Local application/library specific imports.



```python
import csv                     # Standard library imports.
import matplotlib as plt       # Related third party imports.
import numpy                   # Related third party imports.
from mylib import myfunction   # Local application/library specific imports.
```

Wildcard imports (from <module> import *) should be avoided.

### String quotes

Pick a rule and stick to it.


```python
#Yes
a = "hello"
b = "world"
```


```python
#Yes
a = 'hello'
b = 'world'
```


```python
#No
a = 'hello'
b = "world"
```

### Maximum Line Length

Limit all lines to a maximum of 79 characters.
For flowing long blocks of text with fewer structural restrictions (docstrings or comments), the line length should be limited to 72 characters.


```python
with open('/path/to/some/file/you/want/to/read') as file_1, \
     open('/path/to/some/file/being/written', 'w') as file_2:
    file_2.write(file_1.read())
```


```python
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```


```python
if (this_is_one_thing and
    that_is_another_thing):
    do_something()
```


```python
my_list = [a, b,
           c, d
           ]
```


```python
def my_long_function(var_one, var_two,
                     var_three, var_four):
    print(var_one)
```


```python
my_text = ("Do not go gentle into that good night," +
           "Old age should burn and rave at close of day;" +
           "Rage, rage against the dying of the light." +
           "Though wise men at their end know dark is right," +
           "Because their words had forked no lightning they" +
           "Do not go gentle into that good night.")
```


```python
print(my_text)
```

    Do not go gentle into that good night,Old age should burn and rave at close of day;Rage, rage against the dying of the light.Though wise men at their end know dark is right,Because their words had forked no lightning theyDo not go gentle into that good night.
    

### Whitespace in Expressions and Statements


```python
x = 1
y = 2
long_variable = 3
```


```python
submitted += 1
```


```python
a = 10 + 12
b = 10 * 12
c = (10+12) * 12
d = (10)*2 + 2
```


```python
my_list = [1, 2, 3]
```


```python
d = {"Animal": "bird", "age": 13}
```


```python
def my_function(a, b=0):
    return(a + b)
```


```python
a = my_function(10, b=3)
```


```python
if x == 4:
```

### Blank Lines

Surround top-level function and class definitions with two blank lines.


```python
def my_function_a():
    return()


def my_function_b():
    return()
```

Method definitions inside a class are surrounded by a single blank line.


```python
class MyClass():

    def my_function_a():
        return()

    def my_function_b():
        return()
```

Extra blank lines may be used (sparingly) to separate groups of related functions. Blank lines may be omitted between a bunch of related one-liners (e.g. a set of dummy implementations).


```python
def my_function_to_do_this():
    return()


def my_other_function_to_do_this():
    return()




def my_function_to_do_that():
    return()


def my_other_to_do_that():
    return()
```

Use blank lines in functions, sparingly, to indicate logical sections.


```python
def my_function(a, b):
    a = a + 1
    a = a * 2
    a -= 2
    
    b = b + 4
    b = b * 4
    b -= 8
    
    c = a + b
    return(c)
```

## <center> Comments </center>

### Block Comments

Block comments generally apply to some (or all) code that follows them, and are indented to the same level as that code. Each line of a block comment starts with a # and a single space (unless it is indented text inside the comment).


```python
# This is a block comment
a = 0
a = a * 2
a -= 2

# This is a 2 line
# block comment
a = 0
a = a * 2
a -= 2

if a == 0:
    # Block comment are indented to the same level as code
    print(a)
else:
    pass
```

### Inline Comments

An inline comment is a comment on the same line as a statement. Inline comments should be separated by at least two spaces from the statement. They should start with a # and a single space.


```python
a = a * 2   # A useful comment 
```

## <center> Docstring </center>

Code documentation should follows numpy style docstring

https://numpydoc.readthedocs.io/en/latest/format.html

## <center> Naming Conventions </center>

### Class Names


Class names should normally use the CapWords convention.


```python
class MyClass():
    x = 0
```

### Function and Variable Names

Function names should be lowercase, with words separated by underscores as necessary to improve readability.

Variable names follow the same convention as function names.


```python
def my_function():
    return()
```


```python
my_variable = 10
```

### Constants

Constants are usually defined on a module level and written in all capital letters with underscores separating words.


```python
MY_CONSTANT = 10
```

## <center> Tools </center>

http://flake8.pycqa.org/en/latest/


```python
%%cmd 
pip install flake8
```

you can use the command line script:


```python
%%cmd
flake8 my_script.py
```

or use one of the following addon for your code editor:

* Atom : linter-flake 8
* SublimeText : SublimeLinter-flake8
