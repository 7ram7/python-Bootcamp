# Day 1 📚





# 🐍 Python Project Workflow

## 1️⃣ Setup

> The first step before starting to build the project.

### ✅ Tasks

- Create a project directory
- Navigate into the directory
- Create a **Virtual Environment**
- Activate the virtual environment

```bash
mkdir my_project
cd my_project
python3 -m venv venv
source venv/bin/activate
```

### 📌 Why do we use a Virtual Environment?

A **Virtual Environment** isolates each project's dependencies from other projects, preventing version conflicts and making dependency management much easier.

---

## 2️⃣ Dependencies

> In this stage, install all the libraries required for the project.

### Example Libraries

- Flask
- Pandas
- NumPy
- Requests

---

### 📦 What is `pip`?

`pip` is Python's **Package Manager**.

It is responsible for:

- Installing packages
- Updating packages
- Removing packages
- Downloading packages from PyPI

### Example

```bash
pip install requests
```

---

### 📚 Types of Python Libraries

| Type | Description |
|------|-------------|
| **Built-in Libraries** | Libraries that come bundled with Python and require no installation. |
| **Third-party Libraries** | Libraries developed by others and installed using `pip`. |

---

## 3️⃣ Development

> This is where the actual programming begins.

During this stage, you will:

- Write code
- Test the application
- Debug issues
- Add new features and improve the project

Run the application with:

```bash
python3 app.py
```

---

## 4️⃣ Snapshot (`requirements.txt`)

After installing all required libraries, save them into a file called:

```text
requirements.txt
```

### Why?

This allows anyone who clones the project to install **the exact same packages and versions** used during development.

### Generate the file

```bash
pip freeze > requirements.txt
```

> [!WARNING]
> Always generate **requirements.txt** while the **Virtual Environment** is activated.
>
> If you run:
>
> ```bash
> pip freeze
> ```
>
> outside the virtual environment, Python will list every package installed on your system instead of only the project's dependencies.

---

# 🧠 Functions Workflow

## Example

```python
def main():
    student_name = "Ali"
    student_age = "22"

    greet_user(student_name, student_age)


def greet_user(name, age):
    print(f"Welcome {name}, You are {age}")


main()
```

---

## How does Python read this code?

### Stage 1: Reading the file

Python reads the file **from top to bottom**.

While reading, it finds:

- The definition of `main()`
- The definition of `greet_user()`

At this point:

> **No function is executed.**

Python simply stores the function definitions in memory.

---

### Stage 2: Execution begins

When Python reaches:

```python
main()
```

the actual execution starts.

Python calls:

```python
main()
```

---

### Inside `main()`

The following variables are created:

```python
student_name = "Ali"
student_age = "22"
```

Then Python calls:

```python
greet_user(student_name, student_age)
```

The values are passed to the function as follows:

| Parameter | Value |
|-----------|-------|
| `name` | `"Ali"` |
| `age` | `"22"` |

The function effectively becomes:

```python
print("Welcome Ali, You are 22")
```

which prints the output to the console.

---

# Why is `main()` usually placed at the end of the file?

The code works correctly whether `main()` is defined at the top or the bottom.

However, as a **Best Practice**, developers usually:

1. Define all functions first.
2. Call the entry point at the end of the file.

Example:

```python
main()
```

or, even better:

```python
if __name__ == "__main__":
    main()
```

---

## Why?

Not because Python requires it.

It's for the benefit of the **developer**.

When someone opens the file, they can:

1. Read all function definitions.
2. Understand what each function does.
3. Reach the application's entry point at the end.

This makes the code:

- ✅ Easier to read
- ✅ Easier to maintain
- ✅ Easier for other developers to understand
- ✅ More professional

---

# 💡 Important Note

> [!TIP]
> Python **does not execute functions while reading their definitions**.
>
> It simply stores them in memory.
>
> Execution only begins when Python encounters a function call such as:
>
> ```python
> main()
> ```
>
> This is why functions can be defined anywhere in the file, as long as they exist before they are called during execution.
````
