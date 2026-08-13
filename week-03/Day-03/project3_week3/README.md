```python
students=[
    {"name":"rama",
    "score":(100,95),
    "skill":{"python","linux"}
    }
]

for student in students:
    sum=0
    for score in student["score"]:
        sum+=score
        avrage=sum/len(student["score"])
        


student["skill"].add("cybersecurity")
print(f"your name is {student["name"]} and your avrage is {avrage}")
print(student["skill"])
```
