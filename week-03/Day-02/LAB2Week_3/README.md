
```python
def outer():
    cource="python"

    def inneer():
        print(cource)

        inneer()
outer()
        
# LAB 1

course="web devopment bootcamp"
duration=12
def type(course):
    print("opss!")

print(course)
print(duration)
print(type(course))
print(globals())

# LAB 2

building= "tuwaiq"
cohort_size=20
print(f"welcom to {building}, class limit is {cohort_size}")
print("Tuwaiq" in building)
print("cohort_size" in globals())
print(globals()["building"])

# LAB 3

loction="Outter"
def outter():
    print(f"from {loction}")
    def inner():
        loction="Inner"
        print(f"from {loction}")
    inner()
outter()

#  LAB 4

loction=0
def outter():
    loction=1
    print(id(loction))
    print(f"from {loction}")
    def inner():
        nonlocal loction
        loction=2
        print(id(loction))
        print(f"from {loction}")
    inner()
outter()

#  LAB 5

def printer():
    print("welcome")
def desk():
    printer()
def room():
    desk()
def house():
    room()
def city():
    house()
def countery():
    city()

countery()

# LAB 6

languge="python"

def show_lang(languge):
    print(languge)

show_lang("dart")
print(languge)

# LAB 7

rate=0.15
def getTotal(amount):
    total=amount*rate+amount
    return total

print(f"{getTotal(199.99):.2f}")
print(round(getTotal(199.99),2))

# LAB 8

def inspect_order(item,qty):
    subtotal=25*qty
    print(locals())
    print(locals()["subtotal"])
inspect_order("pen" ,10)


```







