

# Python OOP 
- [Project 1](project1_week4/)

## 1. What is OOP?

**OOP (Object-Oriented Programming)** is a programming style where we organize a program around **objects**.

The main idea is to keep:

- **Data** → what the object knows
- **Behavior** → what the object can do

together inside a **class**.

---

# 2. Class vs Object vs Method

## Class

A **class** is a reusable blueprint that defines the structure and behavior of objects.

It describes:

- What data objects should have.
- What actions objects can perform.

```python
class Student:
    pass
```

Think of the class as a **blueprint**, not the actual student.

---

## Object / Instance

An **object** is a concrete instance created from a class.

```python
student = Student()
```

Here:

- `Student` → class
- `student` → object / instance

Each time we call the class with `()`:

```python
student_one = Student()
student_two = Student()
```

we create **two separate objects**.

The variables hold references to those objects.

```python
student_one is student_two
```

This would be:

```text
False
```

because they are different instances.

---

## Method

A **method** is a function defined inside a class.

Methods describe what an object can do.

```python
class Student:

    def introduce(self):
        print("Hello")
```

It is normally called through an object:

```python
student.introduce()
```

### Basic distinction

| Concept | Meaning |
|---|---|
| Class | Blueprint / reusable type |
| Object | One concrete instance |
| Attribute | Data/state belonging to an object or class |
| Method | Behavior/action of an object |

---

# 3. Attributes = Object Data

An **attribute** stores information about an object.

For example, a student may have:

- name
- score

Instance attributes are usually created using `self`.

```python
class Student:

    def __init__(self, name, score):
        self.name = name
        self.score = score
```

The object now has its own:

```text
name
score
```

---

# 4. Creating an Object

Calling a class creates an instance:

```python
student = Student("Sara", 92)
```

The values are passed to the constructor.

The important pattern is:

```python
object = Class(arguments)
```

Each call creates a separate instance.

---

# 5. __init__ — Initializing an Object

`__init__` is used to establish the object's **starting state**.

Python calls `__init__` after creating an instance.

```python
class Student:

    def __init__(self, name, score):
        self.name = name
        self.score = score
```

When we write:

```python
student = Student("Sara", 92)
```

Python creates the object and initializes its attributes using `__init__`.

### Important idea

The constructor parameters receive the starting values.

Then those values are stored in the object:

```python
self.name = name
self.score = score
```

---

# 6. self

`self` refers to the **current object**.

It allows a method to access the data belonging to that particular instance.

```python
class Student:

    def __init__(self, name):
        self.name = name

    def introduce(self):
        print(self.name)
```

When:

```python
student.introduce()
```

Python automatically supplies `student` as `self`.

So:

```python
self
```

means:

> "the object that is currently using this method."

---

## Accessing Instance Attributes

Use:

```python
self.attribute
```

For example:

```python
self.name
self.score
```

This means the attribute belongs to the **current object**.

---

# 7. Instance Methods

An instance method operates on a particular object.

The first parameter is normally:

```python
self
```

Example:

```python
class Student:

    def __init__(self, name, score):
        self.name = name
        self.score = score

    def display_result(self):
        print(self.name, self.score)
```

Call it with:

```python
student.display_result()
```

The object automatically becomes `self`.

### Remember

```text
object.method()
        ↓
self = that object
```

---

# 8. Instance State is Independent

Objects created from the same class share the **same class definition and behavior**, but their instance data is independent.

```python
first = Counter()
second = Counter()
```

If:

```python
first.value += 1
```

only `first.value` changes.

`second.value` remains independent.

### Important rule

> Instance attributes belong to one specific object.

So:

```python
self.value
```

is separate for every instance.

---

# 9. Class Attributes

A **class attribute** is defined directly inside the class body, outside methods.

```python
class Student:

    academy = "Tuwaiq Academy"
```

It is shared as a common value by instances.

It can be accessed through the class:

```python
Student.academy
```

or through an object:

```python
student.academy
```

### Use class attributes for values shared by all instances.

For example:

```python
class Student:
    academy = "Tuwaiq Academy"
```

Every student belongs to the same academy.

---

# 10. Class Attribute vs Instance Attribute

This distinction is extremely important.

## Instance Attribute

Defined using `self`:

```python
self.name = name
```

Each object has its **own value**.

Example:

```text
student1.name → Sara
student2.name → Omar
```

---

## Class Attribute

Defined directly in the class:

```python
academy = "Tuwaiq Academy"
```

It is a shared class-level value.

### Quick comparison

| | Instance Attribute | Class Attribute |
|---|---|---|
| Defined | Usually inside `__init__` | Directly in class |
| Access | `self.name` | `Class.name` |
| State | Separate per object | Shared/default at class level |
| Used for | Object-specific data | Common data |

### Common mistake

Do not use a class attribute when the value is supposed to be different for every object.

---

# 11. Methods Can Change Object State

Methods can calculate information or modify the current object's data.

Example idea:

```python
class Counter:

    def __init__(self):
        self.value = 0

    def increment(self):
        self.value += 1
```

Calling:

```python
counter.increment()
```

changes the state of that specific object.

This is one of the main benefits of OOP:

> The object contains its data and the methods that operate on that data.

---

# 12. Example of Data + Behavior

A small class should normally have a clear responsibility.

For example, a `Student` class can contain:

- student name
- scores
- calculating the average
- adding a valid score

Conceptually:

```python
class Student:

    def __init__(self, name, scores):
        self.name = name
        self.scores = scores

    def average(self):
        # Calculate the student's average
        pass

    def add_score(self, score):
        # Add a valid score
        pass
```

The important idea is not the specific program.

The important idea is:

```text
Student data
     +
Student behavior
     ↓
Student class
```

The class keeps related data and behavior together.

---

# 13. Collections Can Store Objects

Objects can be stored inside normal Python collections.

For example, a list can contain several instances of the same class.

```python
students = [
    Student("Sara"),
    Student("Omar"),
    Student("Lina")
]
```

We can loop through the objects and call their methods:

```python
for student in students:
    student.some_method()
```

This combines normal Python collections with OOP.

### Important idea

A list does not care that its elements are objects.

You can still:

- loop over them
- access their attributes
- call their methods

---

# 14. __str__ — Readable Object Representation

By default, printing an object does not necessarily give a useful human-readable description.

`__str__` allows us to define what should be displayed when the object is converted to a string.

```python
class Student:

    def __init__(self, name, score):
        self.name = name
        self.score = score

    def __str__(self):
        return f"{self.name}: {self.score}"
```

Now:

```python
print(student)
```

uses `__str__`.

### Main purpose

`__str__` gives the object a **clear, human-readable representation**.

Remember:

```text
print(object)
      ↓
__str__()
```

---

# 15. type()

`type()` tells you the object's **exact type/class**.

Example:

```python
type(student)
```

If `student` was created from `Student`, the result represents the `Student` class.

### Main idea

```python
type(object)
```

asks:

> "What is the exact class of this object?"

---

# 16. isinstance()

`isinstance()` checks whether an object belongs to a particular class.

```python
isinstance(student, Student)
```

returns:

```text
True
```

if `student` is an instance of `Student`.

### Difference

```python
type(student)
```

→ tells you the exact type.

```python
isinstance(student, Student)
```

→ checks whether the object is an instance of that class.

### Rule to remember

When inheritance may be involved, `isinstance()` is generally more useful because it checks class membership rather than only comparing the exact type.

---

# 17. Attribute Access

Python allows direct access to attributes by default.

Example:

```python
student.name
student.score
```

Python does not automatically make attributes private.

A leading underscore is commonly used as a convention to indicate that an attribute is intended for internal use.

Example:

```python
self._score
```

The underscore communicates:

> "This is intended to be used internally."

It is mainly a **convention**, not the same as strict private access in some other languages.

---

# 18. Reading an OOP Program

When looking at an OOP program, separate the three main roles:

### 1. Class

Defines the reusable structure and behavior.

```text
Blueprint
```

### 2. Object

A concrete instance created from the class.

```text
Individual instance
```

### 3. Method

Defines an action/behavior that the object can perform.

```text
Behavior
```

A useful way to read OOP code is:

```text
Class
 ↓
Creates Objects
 ↓
Objects have Attributes
 ↓
Objects use Methods
 ↓
Methods can read/change the object's State
```

---

# 19. Common OOP Errors

## Forgetting self

Instance methods normally need `self` as their first parameter.

Incorrect concept:

```python
def introduce():
    ...
```

Correct:

```python
def introduce(self):
    ...
```

Forgetting `self` can cause argument-related errors when the method is called through an object.

---

## Using a Class Attribute for Instance Data

If data should be different for every object, it should normally be an instance attribute.

Incorrect design:

```python
class Student:
    score = 0
```

if every student is supposed to have a different score.

Instead, the score should belong to each instance:

```python
self.score = score
```

---

## Misspelling Attributes

If you accidentally use a different attribute name, you can get an error or unintentionally create a different attribute.

For example:

```python
self.score
```

and later:

```python
self.scores
```

are two different names.

Python does not assume they mean the same thing.

---

## Using an Attribute Before Initialization

An object should have its required starting state established during initialization.

The constructor should create the attributes that the object's methods depend on.

---

# 20. Good Class Design

A good class should have **one clear responsibility**.

Avoid creating one enormous class that tries to manage the entire application.

Instead:

```text
One class
    ↓
One clear responsibility
    ↓
Related data + related behavior
```

For example, a `Student` class should focus on student-related data and behavior.

---

# 21. The Most Important Patterns to Memorize

## Basic Class

```python
class Student:
    pass
```

---

## Creating an Object

```python
student = Student()
```

---

## Constructor

```python
class Student:

    def __init__(self, name):
        self.name = name
```

---

## Instance Method

```python
class Student:

    def introduce(self):
        print("Hello")
```

---

## Calling a Method

```python
student.introduce()
```

---

## Accessing an Attribute

```python
student.name
```

Inside the class:

```python
self.name
```

---

## Class Attribute

```python
class Student:
    academy = "Tuwaiq Academy"
```

---

## __str__

```python
def __str__(self):
    return "Readable description"
```

---

## Checking an Object's Type

```python
type(student)
```

---

## Checking Class Membership

```python
isinstance(student, Student)
```

---

# 22. Exam Cheat Sheet

Before an exam, make sure you can answer these questions:

### What is a class?

A reusable blueprint that defines the structure and behavior of objects.

### What is an object?

A concrete instance created from a class.

### What is an attribute?

Data/state associated with an object or class.

### What is a method?

A function defined inside a class that describes behavior.

### What is `__init__`?

The method used to establish an object's initial state.

### What is `self`?

A reference to the current instance.

### Why do we use `self.name`?

To access or store the `name` belonging to the current object.

### Are two objects created from the same class the same object?

No. Each constructor call creates a separate instance.

### What is a class attribute?

An attribute defined at the class level and available as a shared class-level value.

### What is an instance attribute?

Data belonging to a particular object.

### What does `__str__` do?

Provides a human-readable string representation of an object.

### What does `type()` do?

Reports the object's exact type.

### What does `isinstance()` do?

Checks whether an object is an instance of a specified class.

---

# 23. Mental Model

The easiest way to understand everything from this lesson:

```text
                    CLASS
                     │
          ┌──────────┴──────────┐
          │                     │
        DATA                 BEHAVIOR
     Attributes             Methods
          │                     │
          └──────────┬──────────┘
                     │
                  OBJECT
                     │
          ┌──────────┴──────────┐
          │                     │
      Own State            Uses Methods
     self.name             object.method()
     self.score                  │
          │                      │
          └──────────┬───────────┘
                     │
              State can change
```

## The core idea

> **A class defines what an object is and what it can do.  
> An object is one actual instance of that class.  
> Attributes store its state, and methods define its behavior.**
