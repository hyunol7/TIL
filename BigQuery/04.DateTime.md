날짜 및 시간 데이터
====

### 시간 데이터 다루기
+ 시간 데이터도 세부적으로 나눌 수 있음
+ DATE, DATETIME, TIMESTAMP등
+ DATE : DATE만 표시하는 데이터, 2023-12-31
+ DATETIME : DATE와 TIME까지 표시하는 데이터, Time Zone 정보 없음, 2023-12-31 14:00:00
+ TIME : 날짜와 무관하게 시간만 표시하는 데이터, 23:59:59.00

***
### millisecond, microsecond

```
 SELECT 
  TIMESTAMP_MILLIS(1704176819711) AS milli_to_timestamp_value,
  TIMESTAMP_MICROS(1704176819711000) AS micro_to_timestamp_value,
  DATETIME(TIMESTAMP_MICROS(1704176819711000)) AS datetime_value;

```
![image](https://github.com/user-attachments/assets/cd2f7116-904d-4304-ad72-7a625addedb1)


***
### TIMESTAMP와 DATETIME 비교
+  TIMESTAMP
+  + UTC라고 나옴
   + 한국 시간 -9시간
+ DATETIME
+ + T가 나옴
  + 한국 Zone 사용시 한국 시간과 동일
```
SELECT 
  CURRENT_TIMESTAMP() AS timestamp_col,
  DATETIME(CURRENT_TIMESTAMP(), 'Asia/Seoul') AS datetime_col
```

![image](https://github.com/user-attachments/assets/a7eeced7-0e4b-4514-8ee8-981c5df410b3)

***
### CURRENT_DATETIME
+ CURRENT_DATETIME([time_zone]) : 현재 DATETIME 출력
```
SELECT
  CURRENT_DATE() AS current_date,
  CURRENT_DATE("Asia/Seoul") AS asia_date,
  CURRENT_DATETIME() AS current_datetime,
  CURRENT_DATETIME("Asia/Seoul") AS current_datetime_asia;
```
![image](https://github.com/user-attachments/assets/bd99f796-9b04-498d-946e-27b91077e210)

***
### EXTRACT
+ DATETIME에서 특정 부분만 추출하고 싶은 경우
```
SELECT 
  EXTRACT(DATE FROM DATETIME "2024-01-02 14:00:00") AS date,
  EXTRACT(YEAR FROM DATETIME "2024-01-02 14:00:00") AS year,
  EXTRACT(MONTH FROM DATETIME "2024-01-02 14:00:00") AS month,
  EXTRACT(DAY FROM DATETIME "2024-01-02 14:00:00") AS day,
  EXTRACT(HOUR FROM DATETIME "2024-01-02 14:00:00") AS hour,
  EXTRACT(MINUTE FROM DATETIME "2024-01-02 14:00:00") AS minute,
```
![image](https://github.com/user-attachments/assets/c206adc2-6443-4457-b4a9-e148718c9343)

***
### DATETIME_TRUNC
+ DATE와 HOUR만 남기고 싶은 경우 => 시간 자르기
```
SELECT
  DATETIME "2024-03-02 14:42:13" AS original_data,
  DATETIME_TRUNC(DATETIME "2024-03-02 14:42:13", DAY) AS day_trunc,
  DATETIME_TRUNC(DATETIME "2024-03-02 14:42:13", YEAR) AS year_trunc,
  DATETIME_TRUNC(DATETIME "2024-03-02 14:42:13", MONTH) AS month_trunc,
  DATETIME_TRUNC(DATETIME "2024-03-02 14:42:13", HOUR) AS hour_trunc;
```
![image](https://github.com/user-attachments/assets/5796226d-7806-4cdb-a22e-a396a7d9a870)

***
### PARSE_DATETIM
+ 문자열로 저장된 DATETIME을 DATETIME 타입으로 바꾸고 싶은 경우
```
 SELECT 
  PARSE_DATETIME('%Y-%m-%d %H:%M:%S', '2024-01-11 12:35:35') AS parse_datetime;

```
![image](https://github.com/user-attachments/assets/780369c8-c6c7-4136-8e1d-09b16c0ccbb6)

***
###  FORMAT_DATETIME
+  DATETIME 타입 데이터를 특정 형태의 문자열 데이터로 변환하고 싶은 경우
```
SELECT
  FORMAT_DATETIME("%c", DATETIME "2024-01-11 12:35:35") AS formatted;

```
![image](https://github.com/user-attachments/assets/52badf68-bf18-45d3-81ad-f4ba61efe743)

***
### LAST_DAY
+ 마지막 날을 알고 싶은 경우 : 자동으로 월의 마지막 값을 계산해서 특정 연산을 할 경우
```
  
SELECT 
  LAST_DAY(DATETIME '2024-01-03 15:30:00') AS last_day, 
  LAST_DAY(DATETIME '2024-01-03 15:30:00', MONTH) AS last_day_month, 
  LAST_DAY(DATETIME '2024-01-03 15:30:00', WEEK) AS last_day_week,
  LAST_DAY(DATETIME '2024-01-03 15:30:00', WEEK(SUNDAY)) AS last_day_week_sun,
  LAST_DAY(DATETIME '2024-01-03 15:30:00', WEEK(MONDAY)) AS last_day_week_mon

```
![image](https://github.com/user-attachments/assets/efd6bd33-503e-4f1c-9845-d53eb6c4477c)

***
###  DATETIME_DIFF
+ 두 DATETIME의 차이를 알고 싶은 경우 DATETIME_DIFF(첫 DATETIME, 두번째 DATETIME, 궁금한 차이)
```
 SELECT
  DATETIME_DIFF(first_datetime, second_datetime, DAY) AS day_diff1,
  DATETIME_DIFF(second_datetime, first_datetime, DAY) AS day_diff2,
  DATETIME_DIFF(first_datetime, second_datetime, MONTH) AS month_diff,
  DATETIME_DIFF(first_datetime, second_datetime, WEEK) AS week_diff,
 FROM (
  SELECT
    DATETIME "2024-04-02 10:20:00" AS first_datetime,
    DATETIME "2021-01-01 15:30:00" AS second_datetime,
  )
```
![image](https://github.com/user-attachments/assets/f01000d1-ef43-4c24-8691-8091c5f2cd9b)

