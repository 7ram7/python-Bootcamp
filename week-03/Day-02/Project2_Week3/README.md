# in grades file ⬇️

```python
def calulate_grade(score):
    
        if int(score)>=90:
            print("your score is A")
        elif 90<int(score)>80:
            print("your score is B")
        elif 80<int(score)>75:
            print("your score is C")
        elif 75<int(score)>=70:
            print("your score is D")
        else:
            print("your faild")
   
    
    

        return(int(score))




if __name__== '__main__':
     print(f"you are not in {__name__}")
```

# in the main file ⬇️

```python
import grades
print(grades.calulate_grade(90))
print(grades.calulate_grade(88))
print(grades.calulate_grade(70))
print(grades.calulate_grade(33))
```

# 🛑 important note: 
## the grades file and the main file must be in the same folder
