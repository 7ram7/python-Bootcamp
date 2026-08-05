
# 📘 Day 2 

### Python Syntax & Variables



---

# 🏷️ Variable Naming

A **variable** is a name that refers to a value stored in memory.

## ✅ Variable Naming Rules

Variable names may contain:

- Letters (`A-Z`, `a-z`)
- Numbers (`0-9`)
- Underscores (`_`)

### Valid Examples

```python
student_name = "Sara"

student_age = 20

course = "Python"

user1 = "Ali"

_price = 150
```

---

## ❌ Invalid Variable Names

A variable **cannot** start with a number.

```python
1name = "Sara"
```

Variables **cannot** contain spaces.

```python
student name = "Sara"
```

Variables **cannot** contain special characters.

```python
student-name

student@name
```

---

## 🔠 Python Is Case Sensitive

Python treats uppercase and lowercase letters as different characters.

```python
student_name = "Sara"

Student_name = "Ali"

print(student_name)

print(Student_name)
```

### Output

```text
Sara

Ali
```

Both variables are completely different.

---

## 📖 Naming Convention (Best Practice)

In Python, the recommended naming style is **snake_case**.

```python
student_name = ""

teacher_age = 0

total_price = 0
```

This follows the official Python style guide (**PEP 8**).

---

## 💡 Use Meaningful Variable Names

❌ Poor

```python
a = 20
```

✅ Better

```python
student_age = 20
```

The clearer the variable name, the easier the code is to read and maintain.

---

# 🔒 Constants

Python does **not** have true constants.

Instead, developers follow a naming convention by writing constant names in **UPPERCASE**.

```python
MAX_CLASS_SIZE = 25

MIN_CLASS_SIZE = 15

PI = 3.14159
```

This indicates:

> **This value should not be modified.**

Python will not prevent you from changing it, but doing so violates the common coding convention.

---

# 📝 Comments

Comments begin with the `#` symbol.

```python
# This is a comment
```

Comments are **not executed**.

They are used to:

- Explain code
- Add notes
- Leave reminders for yourself or other developers

---

# 📐 Indentation

Indentation is one of the most important concepts in Python.

Unlike many programming languages, Python does **not** use curly braces (`{}`) to define code blocks.

Instead, it relies on indentation.

---

## Inside an `if` Statement

```python
score = 95

if score >= 90:
    print("Excellent")
```

Notice the **four spaces** before the `print()` statement.

Without proper indentation, Python raises:

```text
IndentationError
```

---

## Inside Functions

```python
def greet():
    print("Hello")
```

Every line inside a function must have the same indentation level.

---

# : (Colon)

A colon (`:`) tells Python that:

> **A new code block starts here.**

### Example

```python
if age >= 18:
    print("Adult")
```

Another example:

```python
def greet():
    print("Hello")
```

Immediately after the colon, Python expects an indented block.

---

# 🖨️ Printing Multiple Lines

Triple quotes allow you to print multiple lines.

```python
print("""
Hello

Python

World
""")
```

### Output

```text
Hello

Python

World
```

---

#  f-Strings

An **f-string** is the recommended way to insert variables into strings.

```python
student_name = "Mada"

age = 20

print(f"My name is {student_name}")
```

### Output

```text
My name is Mada
```

---

You can place any variable inside `{}`.

```python
registered = True

print(f"Status: {registered}")
```

### Output

```text
Status: True
```

---

You can also print multiple variables.

```python
print(f"""
Welcome {student_name}

Age: {age}

Status: {registered}
""")
```

---

## ✅ Advantages of f-Strings

- Easier to read
- Faster than older formatting methods
- Supports all common Python data types

Including:

- `int`
- `float`
- `bool`
- `str`
- `list`
- `tuple`
- `dict`

### Example

```python
price = 25.5

active = True

print(f"Price = {price}")

print(f"Active = {active}")
```

---

# 🔍 `isinstance()`

`isinstance()` checks whether a value belongs to a specific data type.

### Syntax

```python
isinstance(value, type)
```

It accepts two arguments:

1. The value or variable.
2. The data type to compare against.

It returns either:

```python
True
```

or

```python
False
```

---

### Example

```python
age = 20

print(isinstance(age, int))
```

### Output

```text
True
```

---

```python
age = "20"

print(isinstance(age, int))
```

### Output

```text
False
```

---

### More Examples

```python
print(isinstance("Sara", str))

print(isinstance(True, bool))

print(isinstance(5.2, float))
```

---

# ➕ Data Type Compatibility

You cannot directly add a **string** to an **integer**.

```python
age = "20"

print(age + 5)
```

Python raises:

```text
TypeError
```

because it doesn't know how to add text and numbers together.

---

## ✅ Solution 1: Convert the String to an Integer

```python
age = "20"

print(int(age) + 5)
```

### Output

```text
25
```

---

## ✅ Solution 2: Convert the Integer to a String

```python
print(age + str(5))
```

### Output

```text
205
```

> **Note:** This is **string concatenation**, not mathematical addition.
````
