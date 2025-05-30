Class method
==

### Class method 
+ 클래스 레벨에서 호출되는 메서드로, 객체 인스턴스가 아닌 클래스 자체에 작용합니다.
+ 첫 번째 인자로 self가 아닌 cls를 받습니다.
+ 보통 클래스 변수를 접근하거나, **객체를 만드는 대체 생성자(factory method)**로 자주 사용됩니다.

### __repr__
+ 객체를 프린트하거나 출력할 때 문자열로 어떤 모습을 보여줄지 정의하는 특수 메서드

```
class Car:

    def __init__(self, body_type):
        self.body_type = body_type

    def __repr__(self):
        return f'Car({self.body_type} body type)'

    def set_body_type(self, body_type):
        self.body_type = body_type

    @classmethod
    def hyundai(cls):
        return cls("sedam")

print(Car.hyundai())
```
> Car(sedam body type)


### Static Method
+ 클래스나 인스턴스의 상태(cls, self)에 전혀 의존하지 않는 메서드
+ 클래스 안에 있지만 독립적인 유틸리티 함수처럼 작동
```
class Calc:
    def add(x: int, y: int) -> int:
        return x + y

Calc.add = staticmethod(Calc.add)

print('Product:', Calc.add(15,110))

class Calc2:
    @staticmethod
    def add(x: int, y: int)-> int:
        return x + y

print('Product:', Calc2.add(15, 110))
```
>  Product: 125   
>  Product: 125

