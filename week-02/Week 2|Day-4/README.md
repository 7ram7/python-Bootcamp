

# 📘 Week2_Day 4 
Python Conditional Statements Labs

---

# 🧪 LAB 1 - Age Check

```python
age = 20

if age >= 18:
    print("Welcome")

print("Code Completed")
```

---

# 🧪 LAB 2 - Temperature Check

```python
temprator = 31

if temprator >= 35:
    print("Its hot outside")
else:
    print("Cool")
```

---

# 🧪 LAB 3 - Grade System

```python
score = 2000

if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
else:
    print("You need to improve")
```

---

# 🧪 LAB 4 - Boolean Logic

```python
is_active = True
is_verified = True
role = "editor"
is_blocked = False

if is_active and is_verified:
    print("Account is ready")

if role == "admin" or role == "editor":
    print("User can edit")

if not is_blocked:
    print("User is not blocked")
else:
    print("User is blocked")
```

---

# 🧪 LAB 5 - Nested If

```python
account_active = True
has_permission = True

if account_active:
    if has_permission:
        print("Acces Granted")
    else:
        print("Access denied")
else:
    print("Account is not active")
```

---

# 🧪 LAB 6 - Truthy & Falsy

```python
name = "Faisal"
cart = []
balance = 990

if name:
    print("Name has a value")

if not cart:
    print("Your cart is empty, please shop")

print(bool(balance))
```

---

# 🧪 LAB 7 - Name Validation

```python
name = input("Please enter your first name ").strip()

if not name:
    print("Please enter a name")
elif not name.replace(" ", "").isalpha():
    print("Name must contain letters")
else:
    print(f"Valid name {name}")
```

---

# 🧪 LAB 8 - Age Validation

```python
age_text = input("Enter your age: ").strip()

if age_text.isdigit():
    age = int(age_text)
    print(f"You will be {age + 5} in 5 years")
else:
    print("Enter a number")
```

---

# 🧪 LAB 9 - Score Validation

```python
is_score_valid = False

score_text = input("Enter a number between 0 and 100: ")

if score_text.isdigit():
    score_x = int(score_text)

    if score_x >= 0 and score_x <= 100:
        print("Valid score")
        is_score_valid = True
    else:
        print("Score is invalid")
else:
    print("Please enter a number")
```

---

# 🧪 LAB 10 - Membership Check

```python
membership = ["Admin", "Editor", "Viewer"]

current_membership = input("Enter your membership: ").strip().lower()

if current_membership.title() in membership:
    print("You are allowed to view the content")
    print(current_membership)
else:
    print("Please contact admin team")
    print(current_membership)
```

---

# 🧪 LAB 11 - Match Case

```python
command = input("Please enter a command (start, stop, status)").strip().lower()

match command:
    case "start":
        print("......Starting system")

    case "stop":
        print("Stopping sytom....")

    case "status":
        print("System is up and running 👌")

    case _:
        print("Please enter a proper command")
```
