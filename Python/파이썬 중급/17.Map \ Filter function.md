Map \ Filter function
==

### Map function
+ 이터러블의 모든 요소에 함수를 하나씩 적용해서 새 이터레이터 반환

+ 그냥 실행을 했을 때
```
def square(num):
    return num*2

print(square(3))

number_list = {1, 2, 3, 4, 5}

print(map(square, number_list))
```
> 6   
> <map object at 0x000001422AF597E0>


+ for문을 돌렸을 때
```
def square(num):
    return num*2

print(square(3))

number_list = {1, 2, 3, 4, 5}

print(map(square, number_list))

for i in map(square, number_list):
    print(i)
```
![image](https://github.com/user-attachments/assets/dd670872-c925-4348-bd1c-306a8e5691e2)

+ list로 변환도 가능하다
```
print(list(map(square, number_list)))
```
> [2, 4, 6, 8, 10]

+ 함수 두 개를 가져갔을 경우 map function을 만들 때
```
def sum(a, b):
    return a + b

list1 = [2, 4, 6, 8]
list2 = [1,3, 5, 7, 9]
print(list(map(sum, list1, list2)))
```
>[2, 4, 6, 8, 10]   
>[3, 7, 11, 15]


### Filter function 
+ 이터러블의 요소 중, 조건을 만족하는 항목만 남겨 새 이터레이터 반환

```
def is_even(num):
    return num % 2 == 0

number_list = {1, 2, 3, 4, 5}
print(list(filter(is_even, number_list)))
```
> [2, 4]
