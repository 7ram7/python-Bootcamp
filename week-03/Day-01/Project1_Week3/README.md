```python
def calulate_grade(score):
    
    if score.isdigit():
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
    else:
        print("invaled number")
    
    

    return(int(score))

score=input("enter your score:")


print(calulate_grade(score))
```

