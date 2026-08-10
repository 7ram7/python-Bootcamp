
# 🐍 Python Functions 
- [LAB1](LAB_1|Week 3/)

> **Functions** allow you to organize code into reusable blocks that perform specific tasks.
>
> The main idea is:
>
> **Define → Call → Pass Arguments → Execute → Return Result**

---


# 🔹 What is a Function?

A function is a **reusable block of code** designed to perform a specific task.

Instead of writing the same code repeatedly, you can place it inside a function and call it whenever needed.

### Basic Structure

```python
def function_name():
    # code
```

Think of a function as:

```text
Input → Function → Output
```

Not every function needs input or output.

---

# 🔹 Defining a Function

A function is created using the `def` keyword.

```python
def greet():
    print("Welcome to Python")
```

This **defines** the function.

Defining a function does NOT execute it.

The code inside the function runs only when the function is called.

---

# 🔹 Calling a Function

To execute a function, write its name followed by parentheses:

```python
greet()
```

### Important

```python
def greet():
    print("Hello")

greet()
```

The order is:

1. Python reads the function definition.
2. Python reaches the function call.
3. The function executes.
4. Python continues after the function call.

---

# 🔹 Parameters vs Arguments

These two terms are related but different.

## Parameter

A **parameter** is the variable written inside the function definition.

```python
def greet_student(name):
    print(f"Welcome {name}")
```

Here:

```text
name = parameter
```

## Argument

An **argument** is the actual value passed when calling the function.

```python
greet_student("Sara")
```

Here:

```text
"Sara" = argument
```

### Remember

```text
Parameter → variable in the definition
Argument  → actual value passed to the function
```

---

# 🔹 Positional Arguments

When arguments are passed without naming them, their meaning depends on their **position**.

```python
def introduce(name, age):
    print(name)
    print(age)

introduce("Sara", 21)
```

Python matches them by position:

```text
name ← "Sara"
age  ← 21
```

So changing the order can change the meaning:

```python
introduce(21, "Sara")
```

Now:

```text
name ← 21
age  ← "Sara"
```

### Rule

> When using positional arguments, make sure the order matches the parameters.

---

# 🔹 Default Parameters

A parameter can have a default value.

```python
def show_booking(destination="Riyadh", nights=2):
    ...
```

If the caller does not provide a value, Python uses the default.

```python
show_booking()
```

Conceptually:

```text
destination → "Riyadh"
nights      → 2
```

You can also override the defaults:

```python
show_booking("Jeddah", 3)
```

Now:

```text
destination → "Jeddah"
nights      → 3
```

### Why use defaults?

They make a function easier to call when a value is commonly used.

---

# 🔹 `print()` vs `return`

This is one of the most important concepts.

## `print()`

`print()` displays something on the screen.

```python
def greet():
    print("Hello")
```

The function produces visible output, but it does not give that value back to the caller.

---

## `return`

`return` sends a result back to wherever the function was called.

```python
def add(a, b):
    return a + b
```

Now the returned value can be stored:

```python
result = add(5, 3)
```

```text
result = 8
```

### Main Difference

```text
print()  → displays a value
return   → sends a value back
```

A returned value can be:

- stored in a variable
- used in another calculation
- passed to another function
- compared in a condition
- printed later

---

# 🔹 Why `return` is Usually Better for Reusable Functions

Consider:

```python
def calculate(a, b):
    print(a + b)
```

The function only displays the result.

But:

```python
def calculate(a, b):
    return a + b
```

allows the result to be reused:

```python
result = calculate(5, 3)

print(result)
```

Or:

```python
if calculate(5, 3) > 7:
    print("Greater than 7")
```

### Key Idea

> A function that **returns** a result gives the rest of the program control over what to do with that result.

---

# 🔹 `return` Ends the Function

When Python reaches `return`, the current function execution ends immediately.

```python
def example():
    print("First")
    return
    print("Second")
```

Output:

```text
First
```

`"Second"` is never executed.

### Remember

> `return` does two things:
>
> 1. Sends a value back (if provided).
> 2. Immediately ends the current function execution.

---

# 🔹 Functions and Control Flow

Functions do NOT replace `if` statements or loops.

Instead, functions can **contain** them.

For example, a function can contain:

```text
if / elif / else
for
while
variables
calculations
return
```

Example structure:

```python
def count_even(limit):
    count = 0

    for number in range(1, limit + 1):
        if number % 2 == 0:
            count += 1

    return count
```

The important concept is not the specific task.

The important concept is:

```text
Function
│
├── receives input
│
├── performs logic
│   ├── loop
│   └── condition
│
└── returns a result
```

### Key Idea

> Functions organize and package existing programming concepts into reusable components.

---

# 🔹 Functions Can Contain `if / elif / else`

A function can use conditions to decide which result to return.

Conceptually:

```python
def calculate_grade(score):

    if score >= 90:
        return "A"

    elif score >= 80:
        return "B"

    elif score >= 70:
        return "C"

    else:
        return "F"
```

The important idea:

```text
Input
  ↓
Condition checks
  ↓
Choose appropriate result
  ↓
return result
```

The function becomes a reusable decision-making component.

---

# 🔹 Functions Can Contain Loops

A function can also use loops to repeatedly process data.

Conceptually:

```python
def process_data(limit):

    result = 0

    for number in range(limit):
        # process number

    return result
```

The important concept is:

> The function provides a reusable container for the loop and its logic.

Instead of rewriting the loop every time, call the function with different inputs.

---

# 🔹 Function Definition Order

Python needs to know about a function before execution reaches a call to it.

Correct:

```python
def greet():
    print("Hello")

greet()
```

Incorrect:

```python
greet()

def greet():
    print("Hello")
```

### Rule

> Define the function before the program reaches its call during execution.

---

# 🔹 Function Contract

A function has a kind of **contract** between the function and the code calling it.

The contract answers:

```text
What input does the function expect?
What does it do?
What result does it return?
```

For example:

```python
def calculate_grade(score):
    ...
    return grade
```

The function contract can be understood as:

```text
Input:
score

Processing:
Determine the appropriate grade

Output:
grade
```

### Function Contract =

```text
Parameters → Logic → Return Value
```

If the caller or function does not follow this contract, errors can occur.

---

# 🔹 Common Function Errors

Most beginner function errors come from a mismatch between:

```text
Definition ↔ Call ↔ Arguments ↔ Result
```

---

## 1. Missing Required Arguments

If a function requires an argument:

```python
def greet(name):
    ...
```

You must provide it:

```python
greet("Sara")
```

Calling:

```python
greet()
```

causes an error because `name` has no value.

### Rule

> Provide every required argument.

---

## 2. Wrong Positional Argument Order

Given:

```python
def introduce(name, age):
    ...
```

The correct order is:

```python
introduce("Sara", 21)
```

Be careful when parameters have different meanings.

---

## 3. Confusing `print()` with `return`

This:

```python
def calculate():
    print(10)
```

is NOT the same as:

```python
def calculate():
    return 10
```

With `print()`:

```text
10 → displayed
```

With `return`:

```text
10 → sent back to caller
```

---

## 4. Code After `return`

Anything after an executed `return` inside the same function will not run.

```python
def test():
    return 10
    print("Hello")
```

The `print()` is unreachable after the return.

---

## 5. Calling Before Definition

Make sure the function definition is reached before its call.

```python
def greet():
    print("Hello")

greet()
```

---

# 🔹 Combining Functions with Previous Concepts

Functions become much more useful when combined with concepts you've already learned.

A function can combine:

```text
Variables
+
Input
+
Conditions
+
Loops
+
Calculations
+
return
```

This allows you to build small reusable program components.

---

# 🔹 The General Function Pattern

Most functions you write can be understood using this structure:

```python
def function_name(parameter):

    # process the input

    if condition:
        # logic

    for item in something:
        # repeated logic

    return result
```

And then:

```python
result = function_name(argument)
```

Think of it as:

```text
             ARGUMENT
                 ↓
        ┌─────────────────┐
        │    FUNCTION     │
        │                 │
        │     Logic       │
        │   if / loops    │
        │   calculations  │
        │                 │
        └────────┬────────┘
                 ↓
              RETURN
                 ↓
              RESULT
```

---

# 🧠 Quick Review

## Function

Reusable block of code that performs a specific task.

## `def`

Used to define a function.

## Function Call

Executes the function.

```python
function_name()
```

## Parameter

Variable inside the function definition.

```python
def greet(name):
```

`name` is the parameter.

## Argument

Actual value passed during the call.

```python
greet("Sara")
```

`"Sara"` is the argument.

## Positional Arguments

Arguments matched according to their position.

## Default Parameter

A parameter with a predefined value.

```python
def greet(name="Guest"):
```

## `print()`

Displays output.

## `return`

Sends a result back to the caller and ends the current function execution.

## Function + Control Flow

Functions can contain:

```text
if / elif / else
for
while
```

They organize these concepts; they do not replace them.

---



# ⭐ The Most Important Mental Model

When you see a function, think:

```text
1. What does it RECEIVE?
        ↓
2. What does it DO with the input?
        ↓
3. What does it RETURN?
```

For example:

```text
score
  ↓
calculate_grade()
  ↓
if / elif / else
  ↓
grade
```

Or:

```text
limit
  ↓
count_even()
  ↓
loop + condition
  ↓
count
```

The specific task may change, but the function structure remains the same.

> **Functions are mainly about taking input, processing it, and optionally returning a result in a reusable way.**
