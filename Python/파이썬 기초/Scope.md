변수의 엑세스 범위
===


#### Scope
+ 변수나 함수가 유효한 범위, 즉 접근할 수 있는 영역을 말한다
+ local scope / global scope / enclosed scope / enclosing scope

#### local scope와 global scope
+ local scope > 함수 내부에서만 유효
+ global scoep > 프로그램 전체에서 접근 가능
```
my_score = 50  # 🔸 전역 변수 (Global Scope)

def inside_value_function():
    my_score = 80  # 🔹 지역 변수 (Local Scope, 함수 내부)
    print(f"my score inside is {my_score}")

inside_value_function()
print(f"my score outside is {my_score}")
```
> my score inside is 80
> 
> my score outside is 50
