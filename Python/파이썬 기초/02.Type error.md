Type error
==

#### print("Hello" + 1 + "World")
```
    print("Hello" + 1 + "World")
          ~~~~~~~~^~~
TypeError: can only concatenate str (not "int") to str

```
> 타입이 다를 때 나타나는 에러


#### print("Hello" + str(1) + "World")
```
Hello1World
```
> 1을 string으로 타입 변환을 시켜 모두 문자열이 되었기 때문에 에러가 나지 않는다
