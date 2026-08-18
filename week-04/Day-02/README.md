

# Python OOP & File Handling 

- [Project 2](project2_week4/)
- [LAB 2](lab2_week4/)


# 1. Object-Oriented Programming

## Class, Object, and Method

OOP organizes a program around **objects** that contain:

- **Data** → attributes
- **Behavior** → methods

### Class

A **class** is a blueprint that defines the common structure and behavior of objects.

```python
class Student:
    pass
```

The class itself is not an individual student. It describes what a `Student` object can contain and do.

### Object

An **object** is an instance created from a class.

```python
student = Student()
```

Multiple objects can be created from the same class:

```python
student1 = Student()
student2 = Student()
student3 = Student()
```

Each object is an independent instance.

### Method

A **method** is a function defined inside a class. It represents behavior that an object can perform.

```python
class Student:
    def greet(self):
        print("Hello")
```

The method is called through an object:

```python
student.greet()
```

### Remember

**Class = blueprint**  
**Object = instance**  
**Method = behavior/action**

---

## Collections of Objects

A collection such as a list can store multiple objects created from the same class.

```python
students = [
    Student(),
    Student(),
    Student()
]
```

The objects can then be processed using a loop:

```python
for student in students:
    student.some_method()
```

The important idea is that a collection does not only store simple values. It can also store **objects**, allowing the program to work with many instances of a class.

---

# type() and isinstance()

Python provides two useful ways to check object types.

## type()

`type()` tells you the object's exact type/class.

```python
type(student)
```

It answers:

> "What is the exact class of this object?"

---

## isinstance()

`isinstance()` checks whether an object belongs to a particular class.

```python
isinstance(student, Student)
```

It returns:

- `True` → the object belongs to the class
- `False` → it does not

### Main Difference

| Function | Purpose |
|---|---|
| `type()` | Finds the exact type |
| `isinstance()` | Checks whether an object is an instance of a class |

### Important

Prefer `isinstance()` when inheritance may be involved because it can recognize objects belonging to a subclass as well.

---

# Attributes

Attributes are data stored inside an object.

Example:

```python
student.name
student.score
```

Python allows direct access to attributes by default.

```python
student.name
student.score
```

## Underscore Convention

An attribute beginning with `_` is still accessible in Python:

```python
student._score
```

However, the leading underscore convention means:

> "This attribute is intended for internal use."

It is a design convention rather than strict access protection.

---

# Constructor

The constructor is usually implemented using:

```python
__init__()
```

It runs automatically when an object is created.

Its main purpose is to give the object its initial state.

```python
class Student:
    def __init__(self, name, score):
        self.name = name
        self.score = score
```

When creating the object:

```python
student = Student("Sara", 95)
```

Python automatically calls `__init__()`.

The values are stored in the new object's attributes.

### Important Concept

The constructor creates the object's **initial state**.

---

# self

`self` refers to the **current object instance**.

For example:

```python
class Student:
    def __init__(self, name):
        self.name = name
```

Here:

- `name` is the value passed to the constructor.
- `self.name` is the attribute belonging to the current object.

If two objects are created:

```python
student1 = Student("Sara")
student2 = Student("Ali")
```

each object has its own `name` attribute.

### Remember

`self` allows a method to access or modify the data belonging to the current object.

---

# Methods and Object State

A class can contain methods that:

1. Calculate information from the object's data.
2. Modify the object's data.

For example, a student can store several scores and calculate an average.

```python
class Student:
    def __init__(self, name, scores):
        self.name = name
        self.scores = scores

    def average(self):
        return sum(self.scores) / len(self.scores)
```

The method uses the object's own state through `self`.

A method can also update the object:

```python
def add_score(self, score):
    if 0 <= score <= 100:
        self.scores.append(score)
```

The important concept is:

> Objects contain state, and methods can read or change that state.

---

# Class Attributes vs Instance Attributes

An **instance attribute** belongs to one specific object.

```python
self.name
self.score
```

Different objects can have different values.

A **class attribute** belongs to the class and can be shared by instances.

Using a class attribute for data that should belong to each individual object can accidentally cause objects to share state.

### Rule

If the data belongs to each individual object, it should normally be stored as an **instance attribute using `self`**.

---

# Common OOP Errors

## 1. Forgetting `self`

Instance methods need `self` to access the current object's data.

Without it, the method may produce an argument-related error.

---

## 2. Using a Class Attribute Instead of Instance Data

If data should be independent for every object, putting it at class level can accidentally make objects share the same state.

---

## 3. Misspelling Attributes

For example:

```python
self.name
```

and later:

```python
self.nmae
```

are different attribute names.

A typo can cause an error or unintentionally create a new attribute.

---

## 4. Poor Class Boundaries

A class should have a clear responsibility.

Avoid creating one enormous class that tries to manage the entire application.

### Good OOP Design

Keep each class focused on a specific concept or responsibility.

---

# 2. File Handling

Files allow a Python program to preserve data beyond a single program execution.

Normally, variables disappear when the program stops.

A file allows information to remain stored and be used again later.

### Main File Handling Topics

- Paths
- File modes
- Reading
- Writing
- Appending
- Encoding
- Newlines
- Structured data
- Exceptions

---

# Paths and pathlib

A path identifies the location of a file or directory.

Python provides `pathlib` to work with paths using objects.

```python
from pathlib import Path

path = Path("data") / "students.txt"
```

The `/` operator joins path components.

This is clearer and more portable than manually constructing paths with strings.

---

## Relative Paths

A relative path is interpreted from the program's **current working directory**.

For example:

```python
Path("data") / "students.txt"
```

means:

> Look for `data` relative to the current working directory.

---

# Inspecting Paths

Before using a path, you may need to determine what it represents.

### `exists()`

Checks whether the path exists.

```python
path.exists()
```

Returns:

- `True` → exists
- `False` → does not exist

### `is_file()`

Checks whether the path points to a file.

```python
path.is_file()
```

### `is_dir()`

Checks whether the path points to a directory.

```python
path.is_dir()
```

---

# Creating Directories

`mkdir()` creates a directory.

```python
directory.mkdir()
```

If the directory may already exist, use:

```python
directory.mkdir(exist_ok=True)
```

`exist_ok=True` prevents an error when the directory already exists.

---

# File Modes

The file mode determines what Python is allowed to do with the file.

| Mode | Purpose |
|---|---|
| `r` | Read an existing file |
| `w` | Write and replace existing content |
| `a` | Append to existing content |
| `x` | Create a new file; fail if it already exists |

---

## Read Mode: `r`

Use `r` when you want to read an existing file.

```python
with path.open("r", encoding="utf-8") as file:
    content = file.read()
```

Reading does not modify the file.

---

## Write Mode: `w`

Write mode replaces the existing content.

```python
with path.open("w", encoding="utf-8") as file:
    file.write("New content")
```

### Important

If the file already contains data, `w` removes the old content before writing.

Use it only when replacement is intentional.

---

## Append Mode: `a`

Append mode adds new content to the end of the existing file.

```python
with path.open("a", encoding="utf-8") as file:
    file.write("New record\n")
```

The existing content remains.

Append mode is useful for things such as:

- Logs
- Activity records
- Additional entries

---

## Exclusive Creation: `x`

`x` creates a new file.

If the file already exists, Python raises an error.

This is useful when you specifically want to prevent accidentally overwriting an existing file.

---

# with and Context Managers

The `with` statement is the recommended way to work with files.

```python
with path.open("r", encoding="utf-8") as file:
    content = file.read()
```

The `with` block manages the file's lifetime.

When the block finishes, the file is automatically closed.

This also happens if an error occurs inside the block.

### Rule

Keep file operations that depend on the open file **inside the `with` block**.

---

# Reading Files

There are several ways to read text depending on the file size and what you need.

## `read()`

Reads the remaining content as one string.

```python
content = file.read()
```

Best suited for relatively small files.

---

## `Path.read_text()`

A concise alternative for reading text.

```python
content = path.read_text(encoding="utf-8")
```

---

## Reading Line by Line

A file can be iterated over directly:

```python
with path.open("r", encoding="utf-8") as file:
    for line in file:
        ...
```

This processes one line at a time instead of loading the entire file into memory.

### Important

For large files, line-by-line processing is generally more suitable.

---

# `strip()`

When reading lines, they commonly contain a trailing newline.

`strip()` removes surrounding whitespace, including the newline.

```python
name = line.strip()
```

This is useful when each line represents a separate value.

---

# Writing Files

The `write()` method writes text to a file.

```python
file.write("Hello")
```

`write()` returns the number of characters written.

### Important

Writing with mode `w` replaces the previous content.

---

# Appending Files

Appending preserves the existing content and adds new content after it.

```python
with path.open("a", encoding="utf-8") as file:
    file.write("New record\n")
```

A newline is often added between records so that each logical record appears on its own line.

---

# UTF-8 and Newlines

When working with text files, specifying UTF-8 explicitly makes text encoding predictable.

```python
encoding="utf-8"
```

UTF-8 is especially important when files may contain characters from different languages.

---

## Newline Character

The newline character is:

```text
\n
```

It separates logical lines.

For example, multiple names can be combined into separate lines using newline characters.

A final newline is often useful because it keeps later appended content cleanly separated from the previous content.

---

# Structured Data

Plain text works well for simple information, but structured data needs a format that preserves its organization.

Two important formats are:

- **CSV**
- **JSON**

## CSV

CSV represents tabular data using rows and columns.

It is useful for data such as:

- Students
- Scores
- Records
- Tables

## JSON

JSON represents structured data using objects, arrays, and key-value relationships.

It is useful when the relationships and structure of the data need to be preserved.

### Main Idea

Use structured formats when data is more complex than simple lines of text.

---

# Exceptions

File operations can fail for many reasons.

Examples include:

- A file does not exist.
- A directory does not exist.
- A file already exists when using `x`.
- The program does not have permission to access a file.
- The path is invalid.

Python uses **exceptions** to represent these failure situations.

---

## Handling Exceptions

Exceptions can be caught using `try` and `except`.

```python
try:
    ...
except SomeError:
    ...
```

The goal is to make failure paths explicit instead of allowing unexpected errors to terminate the program without handling.

---

## Raising Exceptions

A program can also intentionally raise an exception when an invalid situation occurs.

```python
raise SomeError("Invalid situation")
```

This allows the programmer to clearly communicate that a particular condition should be treated as an error.

---

# 3. Exam Quick Review

## OOP

### Class
A blueprint that defines the structure and behavior of objects.

### Object
An instance created from a class.

### Method
A function defined inside a class that represents object behavior.

### `self`
Refers to the current object instance.

### `__init__()`
Initializes the object's starting state when the object is created.

### Attribute
Data stored on an object.

### `type()`
Returns the exact type of an object.

### `isinstance()`
Checks whether an object belongs to a class.

### Instance Attribute
Data belonging to a specific object.

### Class Attribute
Data belonging to the class and potentially shared between instances.

---

## File Handling

### `Path`
Represents a file or directory path as an object.

### `exists()`
Checks whether a path exists.

### `is_file()`
Checks whether a path is a file.

### `is_dir()`
Checks whether a path is a directory.

### `mkdir()`
Creates a directory.

### `r`
Reads an existing file.

### `w`
Writes and replaces existing content.

### `a`
Adds content to the end of an existing file.

### `x`
Creates a new file and fails if it already exists.

### `with`
Automatically manages the file and closes it after the block.

### `read()`
Reads the remaining file content as one string.

### `read_text()`
Convenient way to read text directly from a `Path`.

### Iterating over a file
Reads the file line by line.

### `strip()`
Removes surrounding whitespace, including trailing newlines.

### `write()`
Writes text to a file and returns the number of characters written.

### UTF-8
A standard text encoding that should be specified explicitly when working with text files.

### `\n`
Represents a newline.

### CSV
Useful for tabular structured data.

### JSON
Useful for structured data with relationships and key-value information.

### Exceptions
Represent errors or failure situations and can be handled using `try`/`except`.

---

# Key Concepts to Memorize

1. **Class = blueprint**
2. **Object = instance of a class**
3. **Method = object behavior**
4. **`self` = current object**
5. **`__init__()` = initialize object state**
6. **`type()` = exact type**
7. **`isinstance()` = belongs to this class?**
8. **Instance attributes belong to individual objects**
9. **`pathlib.Path` represents paths as objects**
10. **`r` = read**
11. **`w` = replace**
12. **`a` = append**
13. **`x` = create only if it does not exist**
14. **`with` = safely manage and automatically close files**
15. **`read()` = entire remaining content**
16. **Iterating over a file = process line by line**
17. **`strip()` = remove surrounding whitespace/newline**
18. **UTF-8 = explicit text encoding**
19. **`\n` = newline**
20. **CSV/JSON = structured data formats**
21. **Exceptions make failure paths explicit**
