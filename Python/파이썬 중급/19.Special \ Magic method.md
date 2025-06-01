Special \ Magic method
===

### Special Method
+ 객체에 여러가지 파이썬 내장 함수나 연산자에 원하는 기능을 부여할 수 있음

### __init__ 
+ 객체가 생성될 때 자동으로 호출되는 생성자 메서드


### __str__
+ string (문자열)
+ 객체를 print(tesla)처럼 출력하려고 할 때 호출되는 메서드
```
class Tesla(object):
    def __init__(self, owner, color):
        self.owner = owner
        self.color = color

    def __str__(self):
        return f"This is {self.color} color {self.owner}'s car"

tesla = Tesla("Joon", "white")
print(tesla)
```
> This is white color Joon's car


### __len__
+ owner의 문자열 길이를 반환한다

```
class Tesla(object):
    def __init__(self, owner, color):
        self.owner = owner
        self.color = color

    def __len__(self):
        return len(self.owner)

tesla = Tesla("Joon", "white")
print(len(tesla))
```
> 4

### __del__
+ 객체가 삭제되거나 소멸될 때 호출되는 메서드
```
class Tesla(object):
    def __init__(self, owner, color):
        self.owner = owner
        self.color = color

    def __str__(self):
        return f"This is {self.color} color {self.owner}'s car"

    def __len__(self):
        return len(self.owner)

    def __del__(self):
        print("This car has been delete")

tesla = Tesla("Joon", "white")
print(tesla)
del tesla
```
> This is white color Joon's car    
> This car has been delete

### __eq__
+ other 라는 parameter를 가져온다
+ 객체 간 비교 연산자 ==가 호출될 때 실행되는 특수 메서드
+ 두 객체으 속성이 같으면 True 다르면 False 반환
```
class Tesla(object):
    def __init__(self, owner, color):
        self.owner = owner
        self.color = color

    def __str__(self):
        return f"This is {self.color} color {self.owner}'s car"

    def __len__(self):
        return len(self.owner)

    def __del__(self):
        print("This car has been delete")

    def __eq__(self, other):
        return self.color == other.color

tesla = Tesla("Joon", "white")
print(tesla)
del tesla

tesla = Tesla("Aail", "red")
print(tesla == tesla)
```
> This is white color Joon's car   
> This car has been delete   
> True    
> This car has been delete

