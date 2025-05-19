JOIN
====

### SQL JOIN
+ 간단하게 "서로 다른 데이터 테이블을 연결하는 것"
+ 공통적으로 존재하는 컬럼이 있다면 JOIN할 수 있음

***
##### INNER JOIN
+ 두 테이블의 공통 요소만 연결

##### LEFT/RIGHT JOIN 
+ 왼쪽/오른쪽 테이블 기준으로 연걸

##### FULL JOIN
+ 양쪽 기준으로 연결

##### CROSS JOIN
+ 두 테이블의 각각의 요소를 곱하기
+ ON 절 사용 안함
![image](https://github.com/user-attachments/assets/2cc72f2e-f4b9-4ce1-af47-51732fb739ba)


***
### 어떤 Table을 왼쪽에 두고, 어떤 Table이 오른쪽에 가야하는지
+ LEFT JOIN의 경ㅇ
+ + 기준이 되는 Table을 왼쪽에 두기
+ 기준에는 기준값이 존재하고, 우측에 데이터를 계속 추가


```
SELECT 
  tp.*,
  t.*
FROM `basic.trainer-pokemon` AS tp
LEFT JOIN `basic.trainer` AS t
ON tp.trainer_id = t.id
```

```
SELECT 
  tp.*,
  t.*, 
  p.*
 FROM `basic.trainer-pokemon` AS tp
 LEFT JOIN basic.trainer AS t
 ON tp.trainer_id = t.id
 LEFT JOIN basic.pokemon AS p
 ON tp.pokemon_id = p.id
```
