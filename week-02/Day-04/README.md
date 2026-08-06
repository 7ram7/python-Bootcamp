
# 📘 Day 4 
Conditional Statements & Input Validation

> Learn how Python makes decisions, evaluates conditions, and validates user input.

---



# 🧠 Programming Logic

Programming is about making decisions.

Every decision starts with a condition that evaluates to:

```text
True
False
```

General syntax:

```python
if condition:
    # code
```

Python evaluates the condition first.

- If `True` → execute the block.
- If `False` → skip it.

---

# Flow of Execution

```text
Condition
    │
 ┌──┴──┐
 │     │
True False
 │     │
 ▼     ▼
Run   Skip
```

---

# if / elif / else

## if

Runs only if the condition is True.

```python
if age >= 18:
    print("Adult")
```

---

## else

Runs when every previous condition is False.

```python
if age >= 18:
    print("Adult")
else:
    print("Minor")
```

---

## elif

Adds additional conditions.

```python
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
else:
    print("Failed")
```

Python checks conditions **from top to bottom**.

The **first True condition** executes.

---

# Order Matters

❌ Bad

```python
if score >= 70:
```

before

```python
elif score >= 90:
```

because `95` will never reach the second condition.

Always place **more specific conditions first**.

---

# Nested if

Use Nested `if` when the second decision depends on the first.

```python
if account_active:

    if has_permission:
        print("Access Granted")
```

---

# Truthy & Falsy

Python automatically converts values into Boolean values using:

```python
bool(value)
```

Falsy values:

```python
False
None
0
0.0
""
[]
{}
()
set()
```

Everything else is Truthy.

---

## Pythonic Style

Instead of

```python
if name != "":
```

write

```python
if name:
```

Instead of

```python
if cart == []:
```

write

```python
if not cart:
```

---

# Validation

Validation means:

> Checking user input before using it.

---

## 1. Presence Validation

```python
if not name:
```

Checks if the user entered something.

---

## 2. Type Validation

### isdigit()

Returns True only if every character is a digit.

```python
"123".isdigit()
```

✅ True

```python
"12.5".isdigit()
```

❌ False

```python
"-5".isdigit()
```

❌ False

---

### isalpha()

Returns True if every character is a letter.

```python
"Python".isalpha()
```

✅ True

```python
"Python3".isalpha()
```

❌ False

For names with spaces:

```python
name.replace(" ", "").isalpha()
```

---

### isnumeric()

Similar to `isdigit()` but supports more Unicode numeric characters.

Most beginner programs use `isdigit()`.

---

# Comparison

| Method | Accepts |
|---------|---------|
| isdigit() | Digits only |
| isalpha() | Letters only |
| isnumeric() | Unicode numeric characters |

---

# Range Validation

Check whether a value falls within a specific range.

Good

```python
if 0 <= score <= 100:
```

Instead of

```python
if score >= 0 and score <= 100:
```

---

# Choice Validation

Use Membership Operators.

```python
roles = ["Admin", "Editor", "Viewer"]

if role.title() in roles:
```

---

# Validation Workflow

```text
Input
   │
strip()
   │
Validate
   │
Convert
   │
Process
```

Never convert before validating.

---

# Common Mistakes

❌

```python
if role == "admin" or "editor":
```

✅

```python
if role == "admin" or role == "editor":
```

Better

```python
if role in ["admin", "editor"]:
```

---

❌

```python
if age = 18
```

✅

```python
if age == 18
```

---

❌

Using `isdigit()` for decimal numbers.

```python
"12.5".isdigit()
```

Returns False.

---

# Best Practices

- Keep conditions simple.
- Validate before converting.
- Use Truthy/Falsy naturally.
- Prefer chained comparisons.
- Normalize input with `strip()`, `lower()`, or `title()`.
- Use `in` for choice validation.

---

# 📝 Cheat Sheet

```python
if
elif
else

and
or
not

bool()

isdigit()
isalpha()
isnumeric()

0 <= score <= 100

if name:

if not cart:

if role in roles:
```

---

# 🎯 Key Takeaways

- Python decisions depend on Boolean values.
- Conditions execute from top to bottom.
- The first True condition wins.
- Empty values are Falsy.
- Validate input before processing it.
- Use `isdigit()`, `isalpha()`, and `isnumeric()` appropriately.
- Use `in` for validating predefined choices.
