


## 1. Python Data Structures
- [LAB 3](lab3_week3/)
- [project 3](project3_week3/)

Python provides several built-in data structures for storing collections of values:

| Structure | Syntax | Main Property |
|---|---|---|
| List | `[]` | Ordered and mutable |
| Tuple | `()` | Ordered and immutable |
| Set | `{}` | Unique elements |
| Dictionary | `{key: value}` | Stores data as key-value pairs |

---

# 2. Lists

A `list` is used to store multiple values in a specific order.

Lists are **mutable**, meaning their contents can be changed after creation.

```python
students = ["Sara", "Neshael", "Dala", "Tife"]
```

---

## Indexing

List indexes start from `0`.

```python
students[0]   # First element
students[1]   # Second element
```

Negative indexes allow you to access elements from the end:

```python
students[-1]  # Last element
students[-2]  # Second-to-last element
```

---

# 3. Slicing

Slicing is used to extract part of a list.

The general syntax is:

```python
list[start:stop:step]
```

- `start` → where to start
- `stop` → where to stop (not included)
- `step` → how many positions to move each time

Example:

```python
car = ["GMC", "BMW", "GEELY", "PORSCHE"]

car[1:3]
```

Result:

```text
["BMW", "GEELY"]
```

---

## Reversing a List

A negative `step` can be used to move backwards through a list:

```python
car[::-1]
```

This reverses the order of the list.

You can also use:

```python
car[-1::-1]
```

to start from the last element and move backwards.

---

# 4. Important List Methods

## `append()`

Adds an element to the end of a list.

```python
task.append("get coffee")
```

---

## `insert()`

Adds an element at a specific index.

```python
task.insert(0, "get breakfast")
```

The first argument is the index, and the second is the value.

---

## `pop()`

Removes an element using its index and returns the removed element.

```python
task.pop(2)
```

If no index is specified, it removes the last element:

```python
task.pop()
```

---

# 5. Looping Through a List

A `for` loop can be used to process every element in a list.

```python
for student in students:
    print(student)
```

The idea is:

> Take each element from `students`, one at a time, and temporarily store it in `student`.

---

# 6. `enumerate()`

`enumerate()` is useful when you need both:

- The index
- The value

at the same time.

```python
for item in enumerate(students):
    print(item)
```

The result is made of tuples:

```text
(0, "Sara")
(1, "Neshael")
(2, "Dala")
(3, "Tife")
```

The structure is:

```text
(index, value)
```

---

## `enumerate()` and `next()`

`enumerate()` creates an iterator.

You can use `next()` to retrieve the next item from that iterator:

```python
iterator = enumerate(students)

next(iterator)
```

This returns the first pair:

```text
(0, "Sara")
```

### Key Idea

```python
enumerate(list)
```

allows you to work with:

```text
index + value
```

instead of only the value.

---

# 7. Tuples

A `tuple` is similar to a list, but it is **immutable**.

```python
numbers = (11, 22, 33, 44, 55, 66)
```

The main difference is:

```text
List  → Mutable
Tuple → Immutable
```

Tuples are useful when you want an ordered collection that should not be modified.

---

# 8. Sets

A `set` stores **unique elements**.

```python
skills = {"python", "flask", "java"}
```

If you add an element that already exists, a duplicate will not be created.

```python
skills.add("python")
```

`"python"` will still exist only once.

### Main Set Properties

- Does not maintain a fixed index-based order.
- Does not allow duplicate elements.
- Is mutable.

---

## Set Methods

### `add()`

Adds an element:

```python
skills.add("HTML")
```

### `remove()`

Removes an element:

```python
skills.remove("java")
```

If the element does not exist, `remove()` raises an error.

### `discard()`

Removes an element:

```python
skills.discard("java")
```

The important difference is that `discard()` does not raise an error if the element does not exist.

---

# 9. Dictionaries

A `dictionary` stores data using:

```text
key : value
```

Example:

```python
student = {
    "name": "Abdullah",
    "age": 22,
    "has_car": True
}
```

Here:

```text
"name"      → key
"Abdullah"  → value

"age"       → key
22          → value
```

You access a value using its key:

```python
student["name"]
student["age"]
```

---

# 10. Dictionary Values

You can retrieve all values from a dictionary using:

```python
student.values()
```

You can also loop through them:

```python
for value in student.values():
    print(value)
```

### Key Idea

`values()` gives you the values stored inside the dictionary.

---

# 11. `type()`

`type()` is used to determine the type of a value or variable.

```python
type(student)
type(student["age"])
```

For example:

```text
dict
int
```

It is especially useful for understanding data types and debugging.

---

# 12. Nested Data Structures

Python allows you to place one data structure inside another.

For example:

```python
students = [
    {
        "name": "Rama",
        "score": (100, 95),
        "skill": {"python", "Linux"}
    }
]
```

The structure is:

```text
students
    ↓
list
    ↓
dictionary
    ├── name → string
    ├── score → tuple
    └── skill → set
```

### Important Idea

Python data structures can be **nested inside each other**.

This is very common when working with real-world data.

---

# 13. Accessing Nested Data

When data structures are nested, you can use multiple operations to reach the desired value.

For example:

```python
student["score"]
```

returns the tuple.

You can then access an element inside the tuple:

```python
student["score"][0]
```

Similarly:

```python
student["skill"]
```

returns the set stored inside the dictionary.

---

# 14. Looping Through Nested Data

Nested loops can be used to process nested structures.

For example:

```python
for student in students:
    for score in student["score"]:
        ...
```

The first loop goes through the students.

The second loop goes through the scores belonging to each student.

---

# 15. Calculating an Average

To calculate the average of multiple scores:

```text
Average = Sum of scores / Number of scores
```

In Python:

```python
total = 0

for score in scores:
    total += score

average = total / len(scores)
```

For example:

```text
100 + 95 = 195

195 / 2 = 97.5
```

### Key Concepts

- `total` accumulates the values.
- `len()` counts the number of values.
- `/` is used to calculate the average.

---

# 16. Built-in Functions

Python provides built-in functions that make working with data easier.

## `sum()`

Calculates the sum of numeric elements:

```python
sum(numbers)
```

## `len()`

Returns the number of elements:

```python
len(numbers)
```

## `max()`

Returns the largest value:

```python
max(numbers)
```

## `min()`

Returns the smallest value:

```python
min(numbers)
```

---

# 17. `sorted()`

`sorted()` is used to sort elements.

```python
sorted(numbers)
```

By default, the values are sorted in ascending order.

For descending order:

```python
sorted(numbers, reverse=True)
```

### Important

`sorted()` returns a **new sorted list**.

It does not directly modify the original list.

---

# 18. `pop()` with Lists

`pop()` does two things:

1. Removes an element.
2. Returns the removed element.

Example:

```python
removed = numbers.pop(2)
```

Now:

```text
removed
```

contains the element that was at index `2`.

---

# 19. The `math` Module

The `math` module provides ready-made mathematical functions.

Import it using:

```python
import math
```

For example:

```python
math.sqrt(100)
```

Result:

```text
10.0
```

---

## Combining Functions

The result of one function can be passed into another function.

For example:

```python
math.sqrt(max(numbers))
```

Python evaluates it conceptually like this:

```text
1. max(numbers)
2. Find the largest number
3. Pass that number to sqrt()
4. Calculate its square root
```

### Key Idea

> A function can receive the result of another function as an argument.

This is an important concept for writing compact expressions.

---

# 20. `__doc__`

Some Python objects, modules, and functions contain documentation.

You can access documentation using `__doc__`.

Example:

```python
math.__doc__
```

This provides documentation related to the `math` module.

### Key Idea

`__doc__` can be used to access the documentation associated with an object or module.

---

# 21. Comparing the Main Data Structures

Memorize this table:

| Type | Ordered | Mutable | Allows Duplicates |
|---|---|---|---|
| List | Yes | Yes | Yes |
| Tuple | Yes | No | Yes |
| Set | No fixed order | Yes | No |
| Dictionary | Key-based | Yes | Keys must be unique |

### Quick Way to Remember

**List**

```text
Ordered + Mutable + Allows duplicates
```

**Tuple**

```text
Ordered + Immutable + Allows duplicates
```

**Set**

```text
Unique elements + Mutable
```

**Dictionary**

```text
Key → Value
```

---



# 22. Final Summary



```text
List
    ↓
Indexing
    ↓
Negative Indexing
    ↓
Slicing
    ↓
append / insert / pop
    ↓
Loops
    ↓
enumerate

Tuple
    ↓
Ordered + Immutable

Set
    ↓
Unique Elements
    ↓
add / remove / discard

Dictionary
    ↓
Key → Value
    ↓
values()

Nested Data Structures
    ↓
List + Dictionary + Tuple + Set

Built-in Functions
    ↓
sum / len / max / min / sorted / type

math Module
    ↓
sqrt()
    ↓
__doc__
```



