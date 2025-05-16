WITH 구문
===

###  WITH 구문
+ CTE라고 표현
+ SELECT 구문에 이름을 정해주는 것과 유사
+ 쿼리 내에서 반복적으로 사용할 수 있음

### WUTH 구문 사용 방법
```
WITH name_a AS (
  SELECT
    col
  FROM Table
 ), name_b AS (
  SELECT
    col2
  FROM Table2
 )
 SELECT
  col
 FROM name_a
```

### PARTITION BY
+ 1) 쿼리 성능 향상
  + 전체 데이터를 스캔하는 것보다 파티션을 설정하는 곳만 스캔하는 것이 더 빠름
+ 2) 데이터 관리 용이성
  + 특정 일자의 데이터를 모두 변경하거나 삭제해야 하면 파티션을 설정해서 삭제할 수 있음
+ 3) 비용
  + 파티션에 해당되는 데이터만 스캔해서 비용을 줄일 수 있음

