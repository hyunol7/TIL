f-string
==

#### 프린트 안에 %s를 넣어서 그 s가 string의 representation
#### %s를 넣어서 %를 넣고 그 다음에 변수를 넣으면 그 변수에 있는 것이 최합이 된다.

>name = "joon"   
>age = 30
-------
>print("Hello, %s" % name)
```
Hello, joon
```
-
#### 두 개의 변수를 넣어서 사용할 수도 있다 
>print("Hello, %s, I am %s" % (name, age))
```
Hello, joon, I am 30
```
#### {}를 사용해서 포지셔닝으로 치환을 하는 방법도 있다
>print("Hello, {}, I am {}" .format(name, age))   
>print("Hello, {1}, I am {0}" .format(name, age))
```
Hello, joon, I am 30
```

#### 딕셔너리 방식 > 자료를 저장하는 방법 중 하나 > key : value 방식
>person = {'name': 'Joon', 'age': 17}
```
Hello, Joon. I am 17.
```

#### 멀티플리케이션 스타 > 스타를 두 번 써가지고 넣었을 때 자동으로 이 person에 있는 딕셔너리가 교환이 된다
>print("Hello, {name}. I am {age}.".format(**person))
```
Hello, Joon. I am 17.
```
#### f-string 방법
>print(f"Hello, {name}. I am {age}.")   
>print(F"Hello, {name}. I am {age}.")   
>print(f"{name.lower()} is cool.")
```
Hello, Joon. I am 17.
Hello, Joon. I am 17.
joon is cool
```
