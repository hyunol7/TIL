PIVOT
===

### PIVOT이 필요한 이유
+ 성능(퍼포먼스)
+ + 자주 나오는 질문 : Python 등에서 처리해도 되지 않을까요?
  + ROW가 많을 경우 = 느려질 수 있음
  + 미리 데이터를 가공해서 ROW를 줄임(네트워크, 데이터 처리 비용의 효율성)
+ 사용이 쉬움
+ + A의 수학 성적을 알고 싶을 때, WHERE 조건에 A를 설정한 후, 수학 컬럼을 선택
+ 데이터 시각화 도구에서 PIVOT한 형태를 지원 : 퍼널 분석에서 확인할 예정

***

### MAX, IF, GROUP BY를 사용한 PIVOT

### IF
```
SELECT
  student, 
  IF(subject="수학", score, NULL) AS 수학,
  IF(subject="영어", score, NULL) AS 영어,
  IF(subject="과학", score, NULL) AS 과학
FROM Table
```

### MAX
```
SELECT
  student, 
  MAX(IF(subject="수학", score, NULL)) AS 수학,
  MAX(IF(subject="영어", score, NULL)) AS 영어,
  MAX(IF(subject="과학", score, NULL)) AS 과학
FROM Table
 GROUP BY
  student
```
