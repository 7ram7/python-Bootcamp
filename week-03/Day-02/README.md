
# 🐍 Python — Scope, Imports & Modules

- [LAB 2](LAB2Week_3/)
- [Project 2](Day-02/Project2_Week3)


---

# 1. Python Scope

**Scope** determines where a variable or name can be accessed in your program.

Python commonly follows the **LEGB rule** when looking for a name:

- **L — Local:** Inside the current function
- **E — Enclosing:** Inside an outer function
- **G — Global:** At the module/file level
- **B — Built-in:** Python's built-in names

### Example

```python
x = "global"

def outer():
    x = "enclosing"

    def inner():
        x = "local"
        print(x)

    inner()

outer()
```

Python searches for `x` starting from the most specific scope and moves outward.

```text
Local → Enclosing → Global → Built-in
```


---

# 2. Local Scope

A variable created inside a function normally belongs to that function's local scope.

```python
def greet():
    name = "Sara"
    print(name)

greet()
```

`name` exists inside `greet()`.

Trying to use it outside the function will normally cause an error:

```python
def greet():
    name = "Sara"

greet()

print(name)   # NameError
```

### Key idea

> Local variables belong to the function where they are created.


---

# 3. Global Scope

A variable created outside functions belongs to the global scope of the module.

```python
name = "Sara"

def greet():
    print(name)

greet()
```

The function can **read** the global variable because Python searches outward when it cannot find the name locally.

### Important distinction

Reading a global variable:

```python
name = "Sara"

def greet():
    print(name)
```

is different from assigning to it:

```python
name = "Sara"

def change():
    name = "Ali"
```

The second `name` is local to `change()`.

It does NOT automatically change the global `name`.


---

# 4. Global Variables and `global`

If you need to modify a global variable from inside a function, use `global`.

```python
count = 0

def increase():
    global count
    count += 1

increase()

print(count)
```

Without `global`, Python treats the assignment as creating/modifying a local variable.

### General rule

Avoid using `global` unnecessarily.

Prefer passing values into functions and returning results:

```python
def increase(count):
    return count + 1

count = increase(count)
```


---

# 5. Nested Functions & Enclosing Scope

A function can be defined inside another function.

```python
def outer():
    location = "Outer"

    def inner():
        print(location)

    inner()

outer()
```

Here:

```text
outer()
 └── inner()
```

`location` belongs to the enclosing function `outer()`.

The inner function can read it because Python searches the **enclosing scope** after checking its local scope.


---

# 6. `nonlocal`

`nonlocal` is used inside a nested function when you want to modify a variable belonging to the **enclosing function**.

```python
def outer():
    location = "Outer"

    def inner():
        nonlocal location
        location = "Inner"

    inner()
    print(location)

outer()
```

Without `nonlocal`:

```python
def outer():
    location = "Outer"

    def inner():
        location = "Inner"
```

`location = "Inner"` creates a **new local variable inside `inner()`**.

With:

```python
nonlocal location
```

Python understands:

> "I want to modify the variable from the enclosing function."


---

# 7. `global` vs `nonlocal`

These keywords modify variables from different scopes.

### `global`

Moves outward to the **module/global scope**.

```python
x = 10

def function():
    global x
    x = 20
```

### `nonlocal`

Moves outward to the **nearest enclosing function scope**.

```python
def outer():
    x = 10

    def inner():
        nonlocal x
        x = 20
```

### Remember

```text
global   → global scope
nonlocal → enclosing function scope
```


---

# 8. `globals()` and `locals()`

Python provides built-in functions that let you inspect namespaces.

### `globals()`

Returns a dictionary representing the global namespace.

```python
name = "Sara"

print(globals()["name"])
```

You can think of it as:

```text
globals()
    ↓
Global names and their values
```

### `locals()`

Returns a dictionary representing the current local namespace.

```python
def example():
    name = "Sara"
    print(locals())

example()
```

### Main idea

```text
globals() → global namespace
locals()  → current local namespace
```


---

# 9. Built-in Names

Python already provides many names that are available without importing anything.

Examples:

```python
print()
len()
type()
id()
round()
sum()
max()
min()
```

These are part of Python's **built-in namespace**.

For example:

```python
print(type("Python"))
```

You don't need:

```python
import something
```

because these functions are built into Python.


---

# 10. Modules

A **module** is usually a `.py` file that contains reusable Python code.

For example:

```text
math_tools.py
```

could contain:

```python
def add(a, b):
    return a + b
```

Another file can import it:

```python
import math_tools

print(math_tools.add(2, 3))
```

### Why modules?

Modules help you:

- Organize code
- Reuse code
- Separate functionality
- Keep large projects manageable


---

# 11. Importing a Module

The basic syntax is:

```python
import module_name
```

Example:

```python
import math

print(math.sqrt(49))
```

The module name is used as a prefix:

```python
math.sqrt()
```

This makes it clear where `sqrt()` came from.


---

# 12. `from ... import ...`

You can import specific names from a module.

```python
from math import sqrt, pi
```

Now you can use:

```python
print(sqrt(49))
print(pi)
```

instead of:

```python
import math

print(math.sqrt(49))
print(math.pi)
```

### Difference

```python
import math
```

uses:

```python
math.sqrt()
math.pi
```

While:

```python
from math import sqrt, pi
```

uses:

```python
sqrt()
pi
```


---

# 13. Avoid Wildcard Imports

Avoid:

```python
from math import *
```

This imports many names without clearly showing where they came from.

For example:

```python
sqrt(49)
```

doesn't immediately tell the reader that `sqrt` came from `math`.

Prefer:

```python
import math

math.sqrt(49)
```

or:

```python
from math import sqrt

sqrt(49)
```

### Why?

Wildcard imports can:

- Hide where names came from
- Cause naming conflicts
- Make code harder to understand
- Make debugging more difficult


---

# 14. Import Aliases

An alias gives an imported module or name another name.

Use:

```python
import datetime as dt
```

Then:

```python
dt.date.today()
```

Instead of:

```python
datetime.date.today()
```

You can also alias individual names:

```python
from math import factorial as fact

print(fact(5))
```

### Good aliases

Aliases should be:

- Short
- Familiar
- Clear
- Unambiguous

Common examples:

```python
import numpy as np
import pandas as pd
import datetime as dt
```

Don't rename imports without a good readability reason.


---

# 15. Standard Library

Python comes with a large collection of ready-made modules called the **Standard Library**.

These modules are included with Python and normally don't require `pip`.

Examples:

```python
import math
import random
import datetime
import statistics
import pathlib
```

Examples of what they provide:

```text
math        → mathematical operations
random      → random values and selections
datetime    → dates and times
statistics  → statistical calculations
pathlib     → working with file paths
```

### Important

Standard library modules are different from third-party packages.

You normally don't need:

```bash
pip install math
```

because `math` is already included with Python.


---

# 16. Module vs Package vs Dependency

These terms are related but different.

### Module

A Python file that organizes reusable code.

```text
calculator.py
```

### Package

A directory that groups related Python modules under a common import structure.

```text
my_package/
    calculator.py
    users.py
    database.py
```

### Dependency

External code that your project relies on.

For example, a project might depend on:

```text
Flask
Requests
NumPy
```

These may need to be installed in the active Python environment.

### Simple mental model

```text
Module
   ↓
One reusable Python file

Package
   ↓
A collection/group of related modules

Dependency
   ↓
Something your project needs in order to work
```


---

# 17. `if __name__ == "__main__":`

This is called the **main guard**.

Example:

```python
def greet(name):
    return f"Hello, {name}!"

if __name__ == "__main__":
    print(greet("Sara"))
```

The important variable here is:

```python
__name__
```

Python automatically gives every module a `__name__`.

---

# 18. What Does `__name__` Contain?

When you run a Python file directly:

```bash
python main.py
```

Python sets:

```python
__name__ == "__main__"
```

So this executes:

```python
if __name__ == "__main__":
    print("Running directly")
```

But if another file imports it:

```python
import main
```

then `__name__` becomes the module's name:

```python
"main"
```

Therefore:

```python
if __name__ == "__main__":
```

will be false.


---

# 19. Why Use the Main Guard?

The main guard separates:

```text
Reusable code
        from
Code that should run when the file is executed directly
```

Example:

```python
def greet(name):
    return f"Hello, {name}!"

if __name__ == "__main__":
    print(greet("Sara"))
```

If another file imports this module:

```python
import greetings
```

the function is available:

```python
greetings.greet("Sara")
```

but the demonstration code inside the main guard doesn't automatically run.

### Common uses

The main guard is useful for:

- Program entry points
- Demonstrations
- Testing
- Example code
- Preventing unwanted execution during imports


---

# 20. Imports and Package Management

A typical Python project may contain:

```text
Project
│
├── main.py
├── utils.py
└── requirements.txt
```

`main.py` may import code from:

```python
import utils
```

And the project may also rely on third-party dependencies installed using:

```bash
pip install package_name
```

The basic workflow is:

```text
Install dependency
       ↓
Python environment
       ↓
Import dependency
       ↓
Use its functionality
```


---

# 21. Import Errors

Import errors usually have a traceable cause.

When an import fails, check:

1. The module name
2. Spelling
3. File location
4. Project structure
5. Active Python environment
6. Whether the requested name exists
7. Whether dependencies are installed


---

# 22. `ModuleNotFoundError`

Example:

```python
import something
```

If Python cannot find the module, you may get:

```text
ModuleNotFoundError
```

Common causes:

```text
Wrong spelling
Wrong location
Package not installed
Wrong Python environment
```

Always check the exact error message first.


---

# 23. `ImportError`

`ImportError` can happen when Python finds the module but cannot import the requested name.

Example:

```python
from math import something
```

If `something` does not exist inside `math`, Python can raise:

```text
ImportError
```

So:

```text
ModuleNotFoundError
→ Python can't find the module

ImportError
→ Python found the module, but the requested import has a problem
```


---

# 24. Avoid Naming Files After Standard Modules

Avoid creating files such as:

```text
random.py
math.py
statistics.py
```

For example, if you create:

```text
random.py
```

and then write:

```python
import random
```

Python may accidentally load your own file instead of the standard-library module.

This can create confusing errors.

### Better

Use names such as:

```text
random_demo.py
math_utils.py
statistics_demo.py
```


---

# 25. Circular Imports

A **circular import** happens when modules depend on each other while loading.

Example:

```text
module_a
   ↓ imports
module_b
   ↓ imports
module_a
```

This creates a cycle:

```text
A → B → A
```

Circular imports can cause confusing import errors because Python is trying to load modules that depend on each other before they have finished loading.

### Better design

Keep shared functionality in a separate module:

```text
A → shared
B → shared
```

instead of:

```text
A → B → A
```

Keep dependencies moving in a clear direction.


---

# 26. Scope + Functions + Imports

These concepts connect together.

For example:

```python
import math

number = 49

def calculate():
    result = math.sqrt(number)
    return result

if __name__ == "__main__":
    print(calculate())
```

Here:

```text
import math
    ↓
Makes the module available

number = 49
    ↓
Global scope

calculate()
    ↓
Creates a local scope

result
    ↓
Local variable

math.sqrt()
    ↓
Uses an imported module

if __name__ == "__main__"
    ↓
Runs the entry-point code only when this file is executed directly
```


---

# 🧠 Quick Mental Model

## Scope

```text
Where can I access this name?

Local
  ↓
Enclosing
  ↓
Global
  ↓
Built-in
```

## Imports

```text
Module
  ↓
import module
  ↓
Use module.name
```

or:

```text
Module
  ↓
from module import name
  ↓
Use name directly
```

## Aliases

```python
import datetime as dt
```

means:

```text
datetime → dt
```

## `global`

```text
Modify a variable from the global scope
```

## `nonlocal`

```text
Modify a variable from an enclosing function
```

## Main Guard

```python
if __name__ == "__main__":
```

means:

```text
"Run this block only when this file is executed directly."
```


---

# 🎯 Key Takeaways

- **Scope** determines where a name can be accessed.
- Python searches names using the **LEGB** rule.
- **Local** variables belong to the current function.
- **Global** variables exist at module level.
- **Enclosing** scope comes from an outer function.
- **Built-in** names are provided by Python.
- `globals()` lets you inspect the global namespace.
- `locals()` lets you inspect the current local namespace.
- `global` allows modification of a global variable from a function.
- `nonlocal` allows modification of a variable from an enclosing function.
- A **module** is a reusable Python file.
- A **package** groups related modules.
- A **dependency** is something the project relies on.
- `import module` keeps the module namespace explicit.
- `from module import name` imports selected names directly.
- Avoid `from module import *`.
- Aliases should improve readability.
- The **Standard Library** comes with Python.
- `if __name__ == "__main__":` separates direct execution from importing.
- `ModuleNotFoundError` usually means Python can't find the module.
- `ImportError` can mean the module exists but the requested name cannot be imported.
- Avoid naming your own files after standard-library modules.
- Avoid circular dependencies between modules.


# ⭐ The Most Important Things to Remember

```text
LEGB
↓
Local → Enclosing → Global → Built-in

global
↓
Modify a global variable

nonlocal
↓
Modify an enclosing-function variable

import module
↓
module.name

from module import name
↓
name

import module as alias
↓
alias.name

if __name__ == "__main__":
↓
Run only when the file is executed directly
```
