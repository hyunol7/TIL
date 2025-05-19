SQL 문법
=====

### - FROM
+ -어떤 테이블에서 데이터를 확인할 것인가?
+ -데이터를 확인할 Table 명시
+ -이름이 너무 길다면 AS "별칭"으로 별칭 지정 가능

### - WHERE
+ -만약 원하는 조건이 있다면 어떤 조건인가?
+ -FORM에 명시된 Table에 저장된 데이터를 필터링(조건 설정) Table에 있는 컬럼을 조건 설정

### -SELECT
+ -테이블의 어떤 컬럼을 선택할 것인가?
+ -데이터를 에 저장되어 있는 컬럼 선택
+ -여러 컬럼 명시 가능
+ -col as "별칭"으로 컬럼의 이름도 지정 가능


### - 데이터가 여러 장소에 저장되어 있는 경우
##### -특정 Table에 있는 데이터를 각각 추출한 후, 연결

```
SELECT : 테이블의 어떤 컬럼을 선택(출력)할 것인가?
  Col1 AS new_name,
  Col2,
  Col3
 FROM Dataset.Table : 어떤 테이블에서 데이터를 확인할 것인가?
 WHERE : 만약 원하는 조건이 있다면 어떤 조건인가?
 Col1 = 1 : 조건문
```

---------------------------------------

### 데이터를 활용하는 과정

![image](https://github.com/user-attachments/assets/9e6a0be6-03a8-47be-b9c6-5b860368dea7)


---------------------------------------

### 집계 : GROUP BY
+ 같은 값끼리 모아서 그룹화 한다
+ + 특정 컬럼을 기준으로 모으면서 다른 컬럼에선 집계 가능(합, 평균, MAX, MIN 등)
    ![image](https://github.com/user-attachments/assets/1eee9d75-11ca-4dc8-8ce3-0bf21c7ea20b)
```
SELECT
  generation
FROM `basic.pokemon`
GROUP BY
  generation
```
---------------------------------------
### DISTINCT : 고유값을 알고 싶은 경우
```
SELECT
  DISTINCT(type1)
FROM `basic.pokemon`

````
---------------------------------------

### WHERE : 조건을 설정하고 싶은 경우
+ Table에 바로 조건을 설정하고 싶은 경우 사용

```
  SELECT
  id
FROM `basic.pokemon`
WHERE 
  type1 = 'Fire'
```
---------------------------------------

### HAVING : 조건을 설정하고 싶은 경우
+ GROUP BY한후 조건을 설정하고 싶은 경우 사용
```
SELECT 
  type1, 
  AVG(attack) AS avg_attack
FROM `basic.pokemon`
GROUP BY type1
HAVING AVG(attack) >= 60;
```

---------------------------------------

### WHERE이랑 HAVING의 차이
+ WHERE
+ + Table에 바로 조건을 설정하고 싶은 경우 사용
```
SELECT eng_name, attack, type1
FROM `basic.pokemon`
WHERE attack >= 60;

```
    
+ HAVING
+ + GROUP BY한 후 조건을 설정하고 싶은 경우 사용
```
SELECT type1, AVG(attack) AS avg_attack
FROM `basic.pokemon`
GROUP BY type1
HAVING AVG(attack) >= 60;
```
---------------------------------------

### ORDER BY : 정렬하기
```
SELECT eng_name, attack
FROM `basic.pokemon`
ORDER BY attack DESC;
```
---------------------------------------

### LIMIT : 출력 갯수 제한하기
```
SELECT eng_name, attack
FROM `basic.pokemon`
ORDER BY attack DESC
LIMIT 5;

```





 

