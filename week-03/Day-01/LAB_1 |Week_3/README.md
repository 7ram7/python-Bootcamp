```python
# Week 3 DAY-1


password=input("pls enter your your password")
while password != "Python123":
    password= input("incorrect password try again:")
print("access granted!")

# LAB 12

for sore in [80,55,45,90]:
    if sore <50:
        pass
    print(f"if passed the score{sore}")

for record in [80,55,45,90]:
    if record <50:
        continue
    print(f"if did not skkiped {sore}")

for badsore in [80,55,45,90]:
    if badsore <50:
        break
    print(f"we saw {badsore}")

# LAB 13

for row in range(1,4):
    for colum in range(1,4):
        print(f"row: {row}, colum: {colum}",)


for row in range(1,4):
    for colum in range(1,4):
        print(f" {row} X {colum},={row*colum}")


# LAB 1 WEEK 3
def greet():
    print("welcome to python")

greet()

# #LAB 2
def show_menu():
    print("1.coffe")
    print("2.tea")
    print("3.ginger")

show_menu()
print("outside of the call")
show_menu()

# #LAB 3
print("line one")
def gotofun():
    print("from within the goto")

print("where is the line 2? ")
gotofun()
print("i'm up here")

#LAB 4

def greet_student(name):
    print(f"welcome {name}")

greet_student("sara and taif")

# LAB 5

def show_booking(destiation="Riyadh",nights=2):
    print(f"you are traviling to {destiation} and will stay for {nights}")
    if nights.isdigit():
        nn=int(nights)
        print(f"you are traviling to {destiation} and will stay for {nn}")

show_booking("jeddah",)
show_booking("Doha",3)


# LAB 6
def getVAT(total,rate=0.15):
    '''this function well get the total with VAT added to it ,and return the sum'''
    finalltotal=total +(total*rate)
    return finalltotal

print(getVAT(154))
print(getVAT(154.,0.05))
print(getVAT.__doc__)
help(getVAT)

```


