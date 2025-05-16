데이터 변환
======

### 데이터 변환을 위한 함수
+ SELECT 문에서 데이터를 변환시킬 수 있음
+  + 또는 WHERE의 조건문에도 사용할 수도 있음
+ 데이터 타입에 따라 다양한 함수가 존재

### 데이터 타입
  ![image](https://github.com/user-attachments/assets/7f0fd284-39b9-40d3-bb1b-4c87c0b9e641)

### 데이터 타입이 중요한 이유
+ 보이는 것과 저장된 것의 차이가 존재
+ 엑셀에서 보면 빈 값 => “”일 수도 있고, NULL일 수도 있음
+ 1이라고 작성된 경우 => 숫자 1일 수도 있고, 문자 1일 수도 있음
+ 2023-12-31 => DATE 2023-12-31일 수도 있고, 문자 2023-12-31일 수도 있음
+ 내 생각과 다른 경우 데이터의 타입을 서로 변경해야 함

### 자료 타입 변경하기
+ 자료 타입 변경하는 함수 : CAST
+ 더 안전하게 데이터 타입 변경하기 : SAFE_CAST

***

### 문자열(STRING) 함수

+ CONCAT : 문자열 붙이기
+ SPLIT : 문자열 분리하기
+ REPLACE : 특정 단어 수정하기
+ TRIM : 문자열 자르기
+ UPPER : 영어 대문자 변환

```
SELECT
  CONCAT("안녕", "하세요") AS concat_example,
  SPLIT("가, 나, 다, 라", ",") AS split_example,
  REPLACE("안녕하세요", "안녕", "실천") AS replace_example,
  TRIM("안녕하세요", "하세요") AS trim_example,
  UPPER("ab") AS upper_example
```
![image](https://github.com/user-attachments/assets/93c75dc0-6d89-4551-8013-9687a1c69420)


