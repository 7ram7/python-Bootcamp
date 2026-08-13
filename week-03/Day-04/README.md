
# Python — Day 4 Notes
## Comprehensions, Conditional Expressions, Filtering & Transformation

> **Exam-focused notes:** This chapter summarizes the concepts covered in today's lectures and labs. The labs are represented through the underlying programming concepts rather than copied as separate exercises.

---

# 1. Comprehensions

A **comprehension** is a concise way to create a new collection from an existing iterable.

Instead of writing a normal loop and manually adding items to a collection, a comprehension expresses the same idea in a compact pattern.

The most common types are:

- List comprehensions
- Set comprehensions
- Dictionary comprehensions

The general idea is:

```python
new_collection = [expression for item in iterable]
```

The comprehension answers three questions:

1. **What should be produced?**
2. **Where do the items come from?**
3. **Should any items be filtered out?**

---

# 2. List Comprehensions

A list comprehension creates a new list.

## Basic Syntax

```python
[expression for item in iterable]
```

### Example concept

```python
numbers = [1, 2, 3, 4, 5]

squares = [number ** 2 for number in numbers]
```

The expression:

```python
number ** 2
```

is applied to every item.

The result is a new list containing the transformed values.

### Equivalent normal loop

```python
squares = []

for number in numbers:
    squares.append(number ** 2)
```

A comprehension is essentially a shorter way to express this pattern.

---

# 3. Transformation

A comprehension can transform every source item into another value.

General pattern:

```python
[transformation for item in iterable]
```

For example, a collection of prices could be transformed by applying VAT:

```python
prices = [10, 25, 40]

prices_with_vat = [
    round(price * 1.15)
    for price in prices
]
```

The important concept is:

> **Each source item produces one transformed result.**

The original collection is not replaced by the comprehension.

---

# 4. Filtering with `if`

A comprehension can include an `if` condition to keep only items that satisfy a condition.

## Syntax

```python
[item for item in iterable if condition]
```

The condition is evaluated for each item.

- `True` → item is included
- `False` → item is skipped

### Example

```python
scores = [42, 67, 91, 58, 75]

passing_scores = [
    score
    for score in scores
    if score >= 60
]
```

Only scores that satisfy:

```python
score >= 60
```

are included.

### Important

Filtering does **not** modify the original collection.

It creates a new collection containing only the selected items.

---

# 5. Transformation + Filtering

A comprehension can transform items while also filtering them.

## Pattern

```python
[expression for item in iterable if condition]
```

The `if` decides **which items survive**.

The expression decides **what value is produced for those items**.

### Example concept

```python
raw_names = [" sara ", "", "OMAR", "lina"]

clean_names = [
    name.strip().title()
    for name in raw_names
    if name.strip()
]
```

Two operations are happening:

### Filtering

```python
if name.strip()
```

Removes empty or whitespace-only names.

### Transformation

```python
name.strip().title()
```

Cleans the name and formats it.

So comprehensions can perform:

```text
Source
  ↓
Filter unwanted items
  ↓
Transform remaining items
  ↓
Create new collection
```

---

# 6. Conditional Expressions

A **conditional expression** chooses one of two values based on a condition.

## Syntax

```python
value_if_true if condition else value_if_false
```

### Example

```python
status = "pass" if score >= 60 else "retry"
```

If:

```python
score >= 60
```

is `True`, the result is:

```text
"pass"
```

Otherwise:

```text
"retry"
```

## Important Difference

A conditional expression produces **one value**.

```python
"pass" if score >= 60 else "retry"
```

A comprehension processes **multiple source items**.

```python
[
    "pass" if score >= 60 else "retry"
    for score in scores
]
```

Therefore:

```text
Conditional expression → chooses one of two values

Comprehension → processes items from an iterable

They can be combined.
```

---

# 7. Conditional Expressions Inside Comprehensions

A conditional expression can be used as the expression part of a comprehension.

Example:

```python
labels = [
    "pass" if score >= 60 else "retry"
    for score in scores
]
```

Every score produces exactly one result.

For example:

```text
42 → retry
67 → pass
91 → pass
```

Unlike a filtering `if`, the `if/else` here does **not remove items**.

It chooses which value to produce.

### Compare

Filtering:

```python
[score for score in scores if score >= 60]
```

Some items disappear.

Conditional expression:

```python
["pass" if score >= 60 else "retry" for score in scores]
```

Every item produces a result.

---

# 8. Multiple `for` Clauses

A comprehension can contain multiple `for` clauses.

## General pattern

```python
[
    expression
    for item1 in iterable1
    for item2 in iterable2
]
```

The clauses are evaluated from **left to right**.

The first `for` behaves like the outer loop.

The second `for` behaves like the inner loop.

### Concept

Suppose we have:

```python
numbers = [1, 2]
letters = ["A", "B"]
```

A comprehension with two `for` clauses generates every possible number/letter combination.

Conceptually:

```text
1 → A
1 → B
2 → A
2 → B
```

This is equivalent to a nested loop:

```python
for number in numbers:
    for letter in letters:
        ...
```

### Important exam rule

> **Read multiple `for` clauses from left to right.**

The first `for` is the outer loop.

The next `for` is nested inside it.

---

# 9. Multiple `for` Clauses and Nested Loops

A comprehension such as:

```python
[
    (number, letter)
    for number in numbers
    for letter in letters
]
```

is conceptually equivalent to:

```python
for number in numbers:
    for letter in letters:
        ...
```

The order matters.

If:

```python
numbers = [1, 2]
letters = ["A", "B"]
```

the resulting pairs follow the nested-loop order:

```text
(1, "A")
(1, "B")
(2, "A")
(2, "B")
```

### Readability Rule

Multiple `for` clauses are useful, but avoid unnecessarily deep comprehensions.

If a normal loop is easier to understand, use the normal loop.

> **Clarity is more important than cleverness.**

---

# 10. Set Comprehensions

A set comprehension creates a **set** instead of a list.

## Syntax

```python
{expression for item in iterable}
```

Notice the curly braces:

```python
{}
```

A set automatically removes duplicate values.

### Example concept

Suppose several email addresses belong to the same domains.

We can extract their domains and store them in a set:

```python
domains = {
    email.split("@")[1].lower()
    for email in emails
}
```

If several emails have the same domain, the domain appears only once.

### Key property

```text
List → duplicates can remain

Set → duplicates are automatically removed
```

---

# 11. Why Sets Remove Duplicates

A set represents a collection of **unique values**.

For example:

```python
values = {1, 2, 2, 3, 3, 3}
```

The resulting set is:

```python
{1, 2, 3}
```

Therefore, set comprehensions are useful when the goal is:

- Uniqueness
- Removing duplicates
- Membership testing
- Collecting unique transformed values

---

# 12. Dictionary Comprehensions

A dictionary comprehension creates key-value pairs.

## Syntax

```python
{key_expression: value_expression for item in iterable}
```

Example concept:

```python
numbers = range(1, 6)

squares = {
    number: number ** 2
    for number in numbers
}
```

The resulting dictionary conceptually contains:

```text
1 → 1
2 → 4
3 → 9
4 → 16
5 → 25
```

The important difference from a list comprehension is that every item produces:

```text
key : value
```

instead of a single value.

---

# 13. Comprehension Types — Quick Comparison

| Type | Syntax | Result |
|---|---|---|
| List comprehension | `[expression for ...]` | List |
| Set comprehension | `{expression for ...}` | Set |
| Dictionary comprehension | `{key: value for ...}` | Dictionary |

### Remember

```python
[expression for item in iterable]
```

→ List

```python
{expression for item in iterable}
```

→ Set

```python
{key: value for item in iterable}
```

→ Dictionary

---

# 14. `for` + `if` Order

For filtering, the normal pattern is:

```python
[expression for item in iterable if condition]
```

The `if` comes **after** the `for` clause.

Example:

```python
[number ** 2 for number in numbers if number % 2 == 0]
```

Conceptually:

```text
Take every number
        ↓
Check whether it is even
        ↓
If yes → square it
        ↓
Put the result in the new list
```

---

# 15. Filtering vs Conditional Expression

This is an important exam distinction.

## Filtering

```python
[number for number in numbers if number > 5]
```

The `if` determines whether the item is included.

Some items may disappear.

```text
Input:  1  2  6  8
Output:       6  8
```

---

## Conditional Expression

```python
["yes" if number > 5 else "no" for number in numbers]
```

The `if/else` determines what value each item produces.

Every item produces a result.

```text
Input:  1   2   6   8
Output: no  no  yes yes
```

### Memorize

```text
if without else → filtering

if ... else → choosing between two output values
```

---

# 16. Comprehensions and Readability

Comprehensions are designed to make simple transformations concise.

Good:

```python
squares = [number ** 2 for number in numbers]
```

Good:

```python
passing_scores = [score for score in scores if score >= 60]
```

But a comprehension should not become unnecessarily complicated.

If the logic is difficult to understand, use a normal loop.

### Principle

> **Correctness and clarity are more important than cleverness.**

---

# 17. Names and Mutable Objects

A variable name is a **reference to an object**.

For example:

```python
a = [1, 2, 3]
b = a
```

`a` and `b` refer to the **same list object**.

They are not two independent lists.

Therefore:

```python
b.append(4)
```

also affects what you see through:

```python
a
```

because both names refer to the same mutable object.

### Important concept

```text
Variable name → reference → object
```

Not:

```text
Variable name = completely separate copy
```

---

# 18. Assignment vs Copy

This distinction is important.

## Assignment

```python
a = [1, 2, 3]
b = a
```

No new list is created.

Both names refer to the same object.

```text
a ──┐
    ├──> [1, 2, 3]
b ──┘
```

---

## Copy

A copy creates a separate outer object.

For example:

```python
b = a.copy()
```

Now:

```text
a ──> [1, 2, 3]

b ──> [1, 2, 3]
```

The two lists are separate objects.

Changing the outer list of `b` does not change the outer list of `a`.

---

# 19. Nested Objects and Shallow Copies

A shallow copy creates a new outer collection, but nested mutable objects can still be shared.

Conceptually:

```text
Original
   ↓
[ [1, 2], [3, 4] ]

Shallow copy
   ↓
[ [1, 2], [3, 4] ]
```

The outer lists are separate, but the nested lists may refer to the same objects.

Therefore:

> **A shallow copy duplicates the outer container, not necessarily everything inside it.**

This matters when working with nested lists, dictionaries, or other mutable structures.

---

# 20. Independent Copies

If nested objects also need to be completely independent, a deeper copy is required.

The important conceptual distinction is:

```text
Shallow copy
→ new outer object
→ nested objects may still be shared

Deep copy
→ nested objects are duplicated as well
→ changes can be independent
```

For exam purposes, remember:

> **Copy depth determines whether nested mutable objects are shared.**

---

# 21. Collection Choice Affects Performance

Different collections have different strengths.

The choice of collection affects:

- Lookup speed
- Updating values
- Uniqueness
- Ordering
- How data is represented

For example:

### List

Good for:

- Ordered sequences
- Index-based access
- Allowing duplicates

### Set

Good for:

- Unique values
- Membership testing
- Removing duplicates

### Dictionary

Good for:

- Key-value relationships
- Looking up values by key
- Updating values associated with keys

### Principle

> Choose a collection based on what the data needs to do, not simply because one syntax is shorter.

---

# 22. Main Ideas From Today's Labs

The exercises today demonstrated several recurring patterns.

## Pattern 1 — Transform every item

```python
[transformation for item in collection]
```

Used for operations such as:

- Squaring numbers
- Applying VAT
- Cleaning or formatting values

---

## Pattern 2 — Keep only matching items

```python
[item for item in collection if condition]
```

Used for operations such as:

- Selecting passing scores
- Keeping valid values
- Removing unwanted entries

---

## Pattern 3 — Transform only valid items

```python
[transformation for item in collection if condition]
```

Used when data must first be filtered and then transformed.

---

## Pattern 4 — Produce one of two values

```python
[value_if_true if condition else value_if_false for item in collection]
```

Used when every source item needs a result, but the result depends on a condition.

---

## Pattern 5 — Generate combinations

```python
[
    expression
    for item1 in collection1
    for item2 in collection2
]
```

Used when every item from one collection needs to be combined with items from another collection.

This follows nested-loop order.

---

## Pattern 6 — Generate unique results

```python
{expression for item in collection}
```

Used when duplicate results should automatically disappear.

---

## Pattern 7 — Generate key-value mappings

```python
{
    key_expression: value_expression
    for item in collection
}
```

Used to create dictionaries programmatically.

---

# 23. Exam Checklist

Before the exam, make sure you can answer all of these:

### Comprehensions

- What is a comprehension?
- What is the basic list comprehension syntax?
- What is the difference between a normal loop and a comprehension?
- How does a comprehension transform values?

### Filtering

- How do you filter values using `if`?
- What happens when the condition is `True`?
- What happens when it is `False`?
- Does filtering modify the original collection?

### Conditional Expressions

- What is the syntax of a conditional expression?
- What is the difference between `if` filtering and `if/else`?
- Does a conditional expression produce one of two values?

### Multiple `for` Clauses

- In what order are multiple `for` clauses read?
- Which `for` acts as the outer loop?
- How does a comprehension with two `for` clauses relate to nested loops?

### Sets

- What is a set comprehension?
- Why do sets remove duplicates?
- When is a set more appropriate than a list?

### Dictionaries

- What is a dictionary comprehension?
- How are key-value pairs generated?

### References and Copies

- What happens when two variables refer to the same mutable object?
- What is the difference between assignment and copying?
- What is a shallow copy?
- Why can nested mutable objects still be shared?
- What is the conceptual difference between shallow and deep copies?

### Collection Choice

- When should you use a list?
- When should you use a set?
- When should you use a dictionary?
- Why does collection choice affect lookup and update behavior?

---

# 24. The Most Important Patterns to Memorize

```python
# List comprehension
[expression for item in iterable]

# Filtering
[item for item in iterable if condition]

# Transformation + filtering
[expression for item in iterable if condition]

# Conditional expression
value_if_true if condition else value_if_false

# Conditional expression inside comprehension
[
    value_if_true if condition else value_if_false
    for item in iterable
]

# Multiple for clauses
[
    expression
    for item1 in iterable1
    for item2 in iterable2
]

# Set comprehension
{expression for item in iterable}

# Dictionary comprehension
{key: value for item in iterable}
```

---

