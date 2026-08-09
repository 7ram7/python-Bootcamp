

# 🔄 Python Loops — Study Notes

Loops allow us to repeat code without writing the same instructions multiple times.


---

### 1. Big Picture — Loops

A loop repeats a block of code multiple times.

Instead of repeating the same instruction manually, write it once and let the loop repeat it.

**Main idea:**

```text
Write instruction once
        ↓
Loop repeats it
        ↓
Less code + less repetition
```

---

### 2. The Two Main Loops

| Loop | Main Idea | Best Used When |
| :--- | :--- | :--- |
| `for` | Iterates through a sequence/range | You know what you want to iterate over |
| `while` | Repeats while a condition is `True` | Repetition depends on a condition |

**Simple rule:**

* Known sequence / number of iterations → `for`
* Condition controls repetition → `while`

---

### 3. for Loop

Used to iterate through a sequence or range.

**Syntax:**

```python
for variable in sequence:
    # code
```

The variable automatically changes on every iteration.

**Example concept:**

```text
sequence
   ↓
item 1
   ↓
item 2
   ↓
item 3
   ↓
...
```

---

### 4. range()

`range()` generates a sequence of numbers and is commonly used with `for`.

**Forms:**

* `range(stop)`
* `range(start, stop)`
* `range(start, stop, step)`

> **Important Rule:** The `stop` value is always excluded.

**Examples:**

```python
range(5)
# Output: 0 1 2 3 4

range(1, 6)
# Output: 1 2 3 4 5

range(2, 11, 2)
# Output: 2 4 6 8 10
```

**Negative step:**

A negative step counts backwards.

```python
range(10, 0, -1)
# Output: 10 9 8 7 6 5 4 3 2 1
```

**Remember:**

* `start` → where to begin
* `stop` → where to stop (excluded)
* `step` → how much to change each time

---

### 5. Loops with Strings and Lists

#### Strings

A string is a sequence of characters, so a `for` loop can process each character individually.

```text
"Python"
   ↓
P → y → t → h → o → n
```

**Key idea:**

```python
for letter in string:
```

*Means:* Take each character one at a time.

---

#### Lists

A `for` loop can also process each list item one by one.

```text
list
 ↓
item 1
 ↓
item 2
 ↓
item 3
```

**Key idea:**

```python
for item in list:
```

*Means:* Take each item from the list one at a time.

---

### 6. while Loop

A `while` loop repeats as long as its condition is `True`.

**Syntax:**

```python
while condition:
    # code
```

**How it works:**

```text
Check condition
      ↓
   True?
   ↙    ↘
 Yes     No
  ↓       ↓
Run     Stop
code
  ↓
Check again
```

> **Important:** Something inside the loop usually needs to change the condition. Otherwise, the loop may never stop.

---

#### ⚠️ Infinite Loop

An infinite loop happens when the condition never becomes `False`.

**Example problem:**

```python
count = 1
while count <= 5:
    print(count)
```

`count` never changes, so the condition remains `True`.

**Correct idea:**

```text
Condition
   ↓
Something changes
   ↓
Condition eventually becomes False
   ↓
Loop stops
```

---

### 7. Validation with while

One of the most important uses of `while` is input validation.

**Main idea:**

Keep asking the user until valid input is provided.

```text
Get input
   ↓
Is it valid?
 ↙       ↘
No       Yes
↓         ↓
Ask      Continue
again
```

**A common pattern:**

```python
value = input("Enter value: ").strip()
while not value.isdigit():
    value = input("Enter value: ").strip()
```

* **`.isdigit()`:** Checks whether a string contains only digits.
  * `"21".isdigit()` → `True`
  * `"abc".isdigit()` → `False`
* **`not`:** Reverses the Boolean value (`True` → `False`, `False` → `True`).

Therefore:

```python
while not value.isdigit():
```

*Means:* Continue while the input is **not** valid digits.

After validation, convert the string:

```python
value = int(value)
```

> **Important:** `input()` always returns a string, even if the user enters a number.

---

### 8. Counters

A counter keeps track of how many times something happens.

**Pattern:**

```python
count = 0
for item in items:
    if condition:
        count += 1
```

**Idea:**

```text
Start at 0
   ↓
Check item
   ↓
Condition true?
   ↓
count += 1
```

**Use a counter when:** You want to know how many items satisfy a condition.

**Examples:**
* How many even numbers?
* How many students passed?
* How many valid inputs?

---

### 9. Accumulators

An accumulator builds a running total or result.

**Pattern:**

```python
total = 0
for item in items:
    total += item
```

**Idea:**

```text
total = 0
   ↓
+ item
   ↓
+ item
   ↓
+ item
   ↓
Final total
```

**Use an accumulator when:** You want to calculate a total/result across multiple iterations.

---

#### Counter vs Accumulator

| Concept | Purpose | Main Pattern |
| :--- | :--- | :--- |
| **Counter** | Counts occurrences | `count += 1` |
| **Accumulator** | Builds a total | `total += value` |

**Easy way to remember:**
* **Counter** → How many?
* **Accumulator** → How much?

---

### 10. Even and Odd Numbers

Use the modulo operator `%` to determine whether a number is even or odd.

```python
number % 2
```

**Logic:**

```text
number % 2 == 0
        ↓
      Even

number % 2 != 0
        ↓
       Odd
```

**Example:**
* `8 % 2 = 0` → Even
* `7 % 2 = 1` → Odd

**Common pattern:**

```python
if number % 2 == 0:
    # Even
else:
    # Odd
```

---

### 11. Labs 1–11 — What They Teach

The labs are practice for the concepts below. Focus on understanding the pattern rather than memorizing the lab code.

| Lab | Main Skill | What You Should Understand |
| :--- | :--- | :--- |
| **Lab 1** | `for` + `range()` | Repeat a fixed number of times and understand why displayed attempts may need `+1` |
| **Lab 2** | `range(start, stop, step)` | Generate even numbers by using a step of 2 |
| **Lab 3** | Negative step | Use a negative step to count backwards |
| **Lab 4** | String iteration | Process each character in a string using `for` |
| **Lab 5** | List iteration | Process each item in a list using `for` |
| **Lab 6** | `if` inside loop | Check every number and classify it as even/odd |
| **Lab 7** | Counter | Count how many items satisfy a condition |
| **Lab 8** | Accumulator | Add multiple values together to produce a total |
| **Lab 9** | Basic `while` | Repeat while a condition is true and update the variable so it eventually stops |
| **Lab 10** | Input validation | Keep asking until the user enters valid numeric input |
| **Lab 11** | `while` condition | Understand how a loop continues/stops based on a variable’s value |

**Lab patterns to remember:**

```text
Lab 1–3
  ↓
for + range()
  ↓
Fixed repetitions / sequences / countdowns

Lab 4–5
  ↓
for + sequence
  ↓
Strings and lists

Lab 6
  ↓
for + if + %
  ↓
Check each item

Lab 7
  ↓
Counter
  ↓
Count matching items

Lab 8
  ↓
Accumulator
  ↓
Calculate total

Lab 9
  ↓
while + variable update
  ↓
Condition-controlled repetition

Lab 10–11
  ↓
while + condition
  ↓
Validation / repeated input
```

---

### 12. Common Mistakes

#### ❌ 1. Forgetting that range() excludes stop

```python
range(1, 5)
# Produces: 1 2 3 4
```

To include 5:

```python
range(1, 6)
```

---

#### ❌ 2. Creating an infinite while loop

**Bad:**

```python
count = 0
while count < 5:
    print(count)
# count never changes
```

**Correct:**

```python
while count < 5:
    print(count)
    count += 1
```

---

#### ❌ 3. Incorrect indentation

Python uses indentation to determine which code belongs to the loop.

**Correct:**

```python
for number in range(5):
    print(number)
```

---

#### ❌ 4. Resetting a counter inside the loop

**Wrong:**

```python
for item in items:
    count = 0  # This resets the counter every iteration!
```

**Correct:**

```python
count = 0
for item in items:
    # condition
    count += 1
```

*Initialize the counter before the loop.*

---

#### ❌ 5. Confusing counters and accumulators

* `count += 1` → Counts occurrences.
* `total += value` → Builds a total.

---

#### ❌ 6. Forgetting input() returns a string

```python
age = input("Age: ")
# Even if the user enters: 21
# Python receives: "21"
```

Convert it when needed:

```python
age = int(age)
```

---

### 13. Quick Revision

#### 🔄 for

Use when iterating over a known sequence/range.

```python
for item in sequence:
    # code
```

---

#### 🔁 while

Use when repetition depends on a condition.

```python
while condition:
    # code
```

---

#### 🔢 range()

```python
range(stop)
range(start, stop)
range(start, stop, step)
```

*Remember: `stop` is excluded.*

---

#### 🔢 Counter

```python
count = 0
for item in items:
    if condition:
        count += 1
```

*Purpose:* Count occurrences.

---

#### ➕ Accumulator

```python
total = 0
for item in items:
    total += item
```

*Purpose:* Build a running total.

---

#### 🔢 Even / Odd

```python
if number % 2 == 0:
    # Even
else:
    # Odd
```

---

#### ✅ Input Validation

```python
value = input("Enter value: ").strip()
while not value.isdigit():
    value = input("Enter value: ").strip()
```

*Purpose:* Keep asking until valid input is provided.

---

### 14. Practice Checklist

Before considering loops mastered, make sure you can:

* [ ] Write a basic `for` loop.
* [ ] Write a basic `while` loop.
* [ ] Explain the difference between `for` and `while`.
* [ ] Use `range()`.
* [ ] Explain why `range(1, 6)` ends at `5`.
* [ ] Use `start`, `stop`, and `step`.
* [ ] Count backwards with a negative step.
* [ ] Loop through a string.
* [ ] Loop through a list.
* [ ] Use `if` inside a loop.
* [ ] Check even/odd numbers using `%`.
* [ ] Create and use a counter.
* [ ] Create and use an accumulator.
* [ ] Count items matching a condition.
* [ ] Calculate a total inside a loop.
* [ ] Validate input using `while`.
* [ ] Understand `.isdigit()`.
* [ ] Understand `not`.
* [ ] Convert validated input using `int()`.
* [ ] Identify and prevent infinite loops.
* [ ] Understand why indentation matters.
* [ ] Combine loops with `if` / `else`.

---

### 15. Core Mental Model

When you see a loop problem, ask yourself:

1. **What am I repeating?**
   * Print? Check? Calculate? Count? Ask the user?
2. **What controls the repetition?**
   * Known sequence → `for`
   * Condition → `while`
3. **Do I need to count something?**
   * `count = 0` then `count += 1`
4. **Do I need a running total?**
   * `total = 0` then `total += value`
5. **What makes the loop stop?**
   * `for` → `range`/sequence eventually ends
   * `while` → condition eventually becomes `False`

---

### 🚀 Core Patterns to Memorize

**Pattern 1 — Repeat a known number of times**

```python
for i in range(5):
    # code
```

**Pattern 2 — Loop through a sequence**

```python
for item in items:
    # code
```

**Pattern 3 — Check every item**

```python
for item in items:
    if condition:
        # code
```

**Pattern 4 — Count matching items**

```python
count = 0
for item in items:
    if condition:
        count += 1
```

**Pattern 5 — Calculate a total**

```python
total = 0
for item in items:
    total += item
```

**Pattern 6 — Repeat while a condition is true**

```python
while condition:
    # code
```

**Pattern 7 — Keep asking until input is valid**

```python
value = input("Enter value: ")
while not value.isdigit():
    value = input("Enter value: ")
```

---

### ⭐ Final Summary

```text
FOR
 ↓
Known sequence / range
 ↓
Repeat through items

WHILE
 ↓
Condition-controlled
 ↓
Repeat while condition is True

COUNTER
 ↓
Counts occurrences
 ↓
count += 1

ACCUMULATOR
 ↓
Builds a running result
 ↓
total += value

VALIDATION
 ↓
Keep asking until input is valid
 ↓
while not condition:
```

> **The key to loops is not memorizing syntax.** Understand what controls the repetition, what changes during each iteration, and what eventually makes the loop stop.
