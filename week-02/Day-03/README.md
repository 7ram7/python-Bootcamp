
# 📘 Day 3 
Operators, Strings & Object Identity

> Learn how Python compares values, checks object identity, works with strings, transforms text, and validates user input.

---





# 🧠 Mental Model

Think of a Python object as having **two different things**:

```
Object
│
├── Value
│     "Python"
│
└── Identity
      Memory Address
```

This distinction explains why Python has both:

- `==` → compares values
- `is` → compares identities

---

# Expressions

## What is an Expression?

An expression is **anything that produces a value**.

Example:

```python
5 + 3
```

produces

```
8
```

More examples

```python
20 / 4

10 > 5

"Py" in "Python"

name.upper()
```

Every one of these returns a value.

---

# Arithmetic Operators

| Operator | Meaning | Example | Result |
|----------|----------|----------|--------|
| + | Addition | 5+3 | 8 |
| - | Subtraction | 8-2 | 6 |
| * | Multiplication | 4*5 |20|
| / | True Division | 5/2 |2.5|
| // | Floor Division |5//2|2|
| % | Modulus |5%2|1|
| ** | Power |2**3|8|

---

## True Division (/)

Always returns a float.

```python
10 / 2
```

Output

```
5.0
```

Even though the answer is a whole number.

---

## Floor Division (//)

Returns only complete groups.

```python
10 // 3
```

Output

```
3
```

because

```
3 × 3 = 9
```

The remainder is ignored.

---

## Modulus (%)

Returns the remainder.

```python
10 % 3
```

Output

```
1
```

Useful for:

- Checking even/odd numbers
- Wrapping values
- Cyclic operations

---

## Exponent (**)

Raises a number to a power.

```python
2 ** 5
```

Output

```
32
```

---

# Operator Precedence

Python follows mathematical order.

Example

```python
4 + 3 * 2
```

NOT

```
14
```

Instead

```
10
```

because multiplication happens first.

Order (simplified)

```
()

**

*  /  // %

+ -

Comparisons

not

and

or
```

Always use parentheses when the expression becomes difficult to read.

Good

```python
total = (price + tax) * quantity
```

---

# Assignment Operators

Assignment operators update an existing variable.

Instead of

```python
x = x + 5
```

use

```python
x += 5
```

---

| Operator | Equivalent |
|----------|------------|
| += | x = x + value |
| -= | x = x - value |
| *= | x = x * value |
| /= | x = x / value |
| //= | x = x // value |
| %= | x = x % value |
| **= | x = x ** value |

---

Example

```python
score = 50

score += 10

print(score)
```

Output

```
60
```

---

# Comparison Operators

Comparison operators always return a Boolean.

```
True

False
```

---

| Operator | Meaning |
|----------|----------|
| == | Equal |
| != | Not Equal |
| > | Greater Than |
| < | Less Than |
| >= | Greater or Equal |
| <= | Less or Equal |

---

Example

```python
age = 20

age >= 18
```

returns

```
True
```

---

# Chained Comparisons

Python allows mathematical style comparisons.

Instead of

```python
age >=18 and age <=60
```

write

```python
18 <= age <= 60
```

Cleaner.

More readable.

Recommended.

---

# Logical Operators

Logical operators combine multiple conditions.

---

## and

Every condition must be True.

```python
age >=18 and age <=60
```

---

## or

At least one condition must be True.

```python
country == "Saudi" or country == "UAE"
```

---

## not

Reverses a Boolean.

```python
not True
```

returns

```
False
```

---

# Membership Operators

Membership operators check whether a value exists inside a container.

Examples of containers

- String
- List
- Tuple
- Set
- Dictionary

---

## in

Returns True if the value exists.

```python
"Py" in "Python"
```

Result

```
True
```

---

```python
5 in [1,2,3,4,5]
```

Result

```
True
```

---

## not in

Returns True if the value does NOT exist.

```python
"Java" not in "Python"
```

Result

```
True
```

---

## ⚠️ Case Sensitive

This is False

```python
"python" in "Python"
```

because

```
P ≠ p
```

Always remember:

Python strings are case-sensitive.

---

# Practical Example

```python
roles = ["Admin","Editor","Viewer"]

role = input().strip().title()

if role in roles:
    print("Access Granted")
else:
    print("Access Denied")
```

---

## Why use

```python
.strip().title()
```

Because users may type

```
admin

ADMIN

 admin

AdMiN
```

All become

```
Admin
```

making validation reliable.

---

# Common Mistakes ⚠️

❌

```python
if "python" in "Python":
```

Wrong expectation.

Returns

```
False
```

---

Better

```python
if "python" in text.lower():
```

---

# Best Practice ✅

Normalize user input before comparison.

```python
username = input().strip().lower()
```

This removes unnecessary spaces and makes comparisons consistent.

---

# Mini Challenge 💪

Predict the output.

```python
text = "Python"

print("Py" in text)

print("Java" in text)

print("python" in text)
```

Think before running the code.

---

# Quick Cheat Sheet

```python
in
not in

==
!=
<
>
<=
>=

and
or
not

+=
-=
*=
/=
```

---

➡️ **End of Part 1**

Next Part:
- Identity Operators (`is`, `is not`)
- `==` vs `is`
- `id()`
- Immutable vs Mutable
- Memory Model
- `None`
- Variable Swapping


-------------------------------------------------------------------------------------------------------------------------------------------
# 📘 Day 3 - Part 2
# Identity Operators, Object Identity & Memory

---

# 🧠 Mental Model

This lesson is about answering **two completely different questions**.

Imagine you have two identical phones.

```
Phone A 📱
Color: Black
Storage: 256GB

Phone B 📱
Color: Black
Storage: 256GB
```

Question 1:

> Do they have the same specifications?

Answer:

```
Yes
```

Question 2:

> Are they literally the same physical phone?

Answer:

```
No
```

Python asks these exact same questions.

---

# Equality vs Identity

```
==  → Compare VALUE

is  → Compare OBJECT
```

Never confuse them.

---

# Equality Operator (==)

## Purpose

Checks whether **two values are equal.**

It does NOT care where they live in memory.

---

Example

```python
x = [1, 2]

y = [1, 2]

print(x == y)
```

Output

```python
True
```

Because

```
[1,2]

equals

[1,2]
```

Same values.

---

Memory representation

```
Memory

Object A

[1,2]


Object B

[1,2]
```

Different objects.

Same contents.

Therefore

```
==

returns True
```

---

# Identity Operator (is)

## Purpose

Checks whether **two variables point to the exact same object.**

Not the same value.

The same object.

---

Example

```python
x = [1,2]

y = x

print(x is y)
```

Output

```
True
```

because

```
x

↓

Object

[1,2]

↑

y
```

Both names point to ONE object.

---

Example 2

```python
x = [1,2]

y = [1,2]

print(x is y)
```

Output

```
False
```

because

```
Object A

[1,2]



Object B

[1,2]
```

Two different objects.

---

# Visual Comparison

```
x = [1,2]

y = [1,2]
```

```
x

↓

[1,2]



y

↓

[1,2]
```

```
x == y

True

x is y

False
```

---

Now

```python
x = [1,2]

y = x
```

becomes

```
x
 \
  \
   ↓

[1,2]

   ↑
  /
 /

y
```

Now

```
x == y

True

x is y

True
```

---

# Rule to Remember

```
==

asks

"Do you look the same?"


is

asks

"Are you literally the same object?"
```

---

# Why Does Python Have Both?

Sometimes we only care about values.

Example

```python
password == "admin"
```

Obviously we don't care where the string is stored.

---

Sometimes we care about identity.

Example

```python
value is None
```

We are checking whether the object is literally the special object called None.

---

# id()

Every object has an identity.

Python exposes it using

```python
id()
```

---

Example

```python
x = [1,2]

print(id(x))
```

Output

```
140736287851768
```

This number is unique during the object's lifetime.

Think of it as

```
Object ID
```

---

Example

```python
x = [1,2]

y = x

print(id(x))

print(id(y))
```

Output

```
140736287851768

140736287851768
```

Same identity.

Same object.

---

Example

```python
x = [1,2]

y = [1,2]

print(id(x))

print(id(y))
```

Output

```
140736287851768

140736287850960
```

Different IDs.

Different objects.

---

# Immutable Objects

## Definition

Immutable means

```
Cannot change after creation.
```

If you modify it...

Python creates

```
A NEW OBJECT
```

instead.

---

Examples

```
str

int

float

bool

tuple
```

---

Example

```python
name = "Python"

name = name.replace("Python","Java")
```

Python does NOT modify

```
"Python"
```

Instead

It creates

```
"Java"
```

as a completely new object.

---

Visual

```
Before

name

↓

"Python"



After

name

↓

"Java"


The old object still exists until garbage collected.
```

---

# Mutable Objects

Mutable means

```
Can be modified
```

without creating another object.

---

Examples

```
list

dict

set
```

---

Example

```python
numbers = [1,2]

numbers.append(3)
```

Python changes

```
[1,2]

↓

[1,2,3]
```

Same object.

Same identity.

---

# Why is This Important?

Imagine

```python
x = [1,2]

y = x

x.append(3)
```

Question

What is

```
y
```

?

Answer

```
[1,2,3]
```

Why?

Because

```
x

↓

Object

[1,2,3]

↑

y
```

They share one object.

---

# None

None means

```
No value

Nothing

Empty reference
```

It is NOT

```
0

False

""

[]
```

All of these are different.

---

Correct comparison

```python
if value is None:
```

NOT

```python
if value == None:
```

Using

```
is
```

is the recommended Python style.

---

Example

```python
status = None

if status is None:
    print("No status yet")
```

---

# Variable Swapping

Python has a beautiful feature.

Instead of

```python
temp = x

x = y

y = temp
```

Simply write

```python
x, y = y, x
```

Example

```python
x = 5

y = 10

x, y = y, x
```

Result

```
x = 10

y = 5
```

---

# Common Mistakes ⚠️

❌

```python
if x is 5:
```

Don't use

```
is
```

for numbers.

---

Correct

```python
if x == 5:
```

---

❌

```python
if username is "Ali":
```

Wrong.

---

Correct

```python
if username == "Ali":
```

---

Correct use of is

```python
if value is None:
```

---

# Best Practice ✅

Use

```
==
```

for

- strings

- integers

- floats

- user input

- calculations

Use

```
is
```

only for

- None

- checking shared objects

- object identity

---

# Memory Trick 🧠

Remember this sentence forever:

```
==

Same VALUE


is

Same OBJECT
```

---

# Mini Challenge 💪

Predict the output.

```python
x = [1,2]

y = [1,2]

print(x == y)

print(x is y)
```

---

Now

```python
x = [1,2]

y = x

print(x == y)

print(x is y)
```

Can you explain WHY?

---

# Cheat Sheet

```
==

Compare values


is

Compare identities


id()

Return object identity


Immutable

Creates NEW object


Mutable

Changes SAME object


None

Compare using

is None
```

---

✅ End of Part 2

Next Part:
- String Indexing
- String Slicing
- Negative Indexes
- Step
- Reverse Strings
- All String Methods (`strip`, `lower`, `upper`, `title`, `replace`, `find`, `startswith`, `endswith`, `split`, `join`)
- Labs Explained
