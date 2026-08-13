
```python

# LAB 1
import math 

student=["sara","neshael","dalal","tife"]

for students in student:

    print(student)


for iterable in enumerate(student):   
    print(iterable)

iterable= enumerate(student)
print(next(iterable))

# LAB 2
set_col={"abdullah","nasser","dalal","sara"}
tuple_col=(11,22,33,44,55,66,)
dict_col={"name":"Abdullah","age":22,"has car":True}
list_col=["ABC",333,(33.33)]


for c in dict_col.values():
    print(type(c))


print(set_col)
print(tuple_col)
print(list_col)
print(type(set_col))
print(type(tuple_col))
print(type(list_col))

# LAB 3
car=["GMC","BMW","GEELY","PORSCHE"]
print(car[3])
print(car[-1])
print(car[-1::-1])

# LAB 4
task=["read email","open ticket"]

task[0]="login"
task.append("get coffe")
task.insert(0,"get breakfast")
print(task)
task.pop(3)
print(task)

# LAB 5 
nums=[11.22,33,44,55,66]

print(sum(nums))
print(len(nums))
print(max(nums))
print(min(nums))
print(math.sqrt(max(nums)))
print(math.__doc__)
print(nums.pop(2))
print(sorted(nums,reverse=True))

# LAB 6
skills={"python","flask","java","fastAPI","django"}
skills.add("CSS")
skills.add("HTML")
skills.remove("java")
skills.discard("java")
print(skills)

```
