```python
# class student:
#     pass

# print(student)
# print(type(student))

# class student:
#     pass

# student_one=student()
# student_two=student()


# print(student_one)
# print(student_one is student_two)

# class student:
#     def __init__(self,name,score):
#         self.name=name
#         self.score=score

# student=student("sara","92")

# print(student.name)
# print(student.score)


# class Student:
#     def __init__(self,name):
        

#         self.name=name
#     def introduce(self):
#         print(f"i am {self.name}")

# student=Student("omar")
# student.introduce()




# class student:
#     def __init__(self,name,score):
#         self.name=name
#         self.score=score

# sara=student("sara","92")
# omar=student("omar","81")

# sara.score=95

# print(sara.score)
# print(omar.score)

# print(omar is sara)
# print(isinstance(omar,student))

# class student:
#     academy="Twaiq academy"
#     def __init__(self,name):
#         self.name=name

# sara=student("sara")
# print(student.academy)
# print(sara.academy)


# class Student:
#     def __init__(self,name,score):
#         self.name=name
#         self.score=score
#     def display_result(self):
#         print(self.name,self.score)

# student=Student("lina",88)
# student.display_result()

# class Counter:
#     def __init__(self):
#         self.value=0
#     def increment(self):
#         self.value+=1

    
# counter=Counter()
# counter.increment()
# counter.increment()
# print(counter.value)

        
# class Rectangle:
#     def __init__(self,width,hight):
#         self.width=width
#         self.hight=hight
#     def area(self):
#         return self.width * self.hight

# rectangel= Rectangle(5,3)
# print(rectangel.area())

# class BankAccount:
#     def __init__(self,balance=0):
#         self.balance=balance

#     def withdraw(self,amount):
#         if amount <=0 or amount >self.balance:
#             return False
        
#         self.balance-=amount
#         return True
    

# account=BankAccount(500)
# print(account.withdraw(200))
# print(account.withdraw(200))
        

# class Student:
#     def __init__(self,name,score):
#         self.name=name
#         self.score=score

#     def __str__(self):
#         return f"{self.name}:{self.score}"
    
# student=Student("sara",90)
# print(student)
        
# class Counter:
#     def __init__(self):
#         self.value=0
#     def increment(self):
#         self.value+=1

# first=Counter()
# second=Counter()

# first.increment()

# print(first.value)
# print(second.value)


# class Student:
#     def __init__(self,name):
#         self.name=name
        

#     def greet(self):
#         return f" hello {self.name}"


# students=[
#     Student("sara"),
#     Student("omar"),
#     Student("lina")
# ]
# for student in students:
#     print(student.greet())

# class Student:
#     pass

# student=Student()
# print(type(student))
# print(type(student)is Student)

# print(isinstance(student,Student))

# class Student:
#     def __init__(self,name,score):
#         self.name=name
#         self._score=score

# student=Student("sara",95)
# print(student.name)
# print(student._score)

# class Student:
#     def __init__(self,name,scores):
#         self.name=name
#         self._scores=scores
    
#     def average(self):
#         return sum(self.scores)/len(self._scores)
    
#     def add_score(self,score):
#         if 0<=score <=100:
#             self._scores.append(score)

# student=Student("sara",[90,80])
# student.add_score(100)
# print(student.name,student.average())
    




class Student:

    def __init__(self, name):
        self.name = name
        self.scores = []

    def add_score(self, score):
            if 0 <= score <= 100:
                self.scores.append(score)

     
    def average(self):
            if not self.scores:
                return 0
            return sum(self.scores) / len(self.scores)


class Course:
    def __init__(self):
        self.students = []

    def add_student(self, student):
        self.students.append(student)

    def display_students(self):
        for student in self.students:
            print(f"Name: {student.name}")
            print(f"Scores: {student.scores}")
            print(f"Average: {student.average():.2f}")
            



sara = Student("Sara")
sara.add_score(99)
sara.add_score(98)

rama = Student("rama")
rama.add_score(97)
rama.add_score(93)


course = Course()

course.add_student(sara)
course.add_student(rama)

course.display_students()
```
