```python
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
