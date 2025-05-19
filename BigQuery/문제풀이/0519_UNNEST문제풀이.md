#### 1) array_exercises 테이블에서 각 영화(title)별로 장르(genres)를 UNNEST해서 보여주세요

```
SELECT
  title,
  genre
FROM `advanced.array_exercises`
CROSS JOIN UNNEST(genres)
AS genre
```

#### 2) array_exercises 테이블에서 각 영화(title)별로 배우(actor)와 배역(character)을 보여주세요. 배우와 배역은 별도의 컬럼으로 나와야 합니다
```
SELECT
  title,
  actor,
  character
FROM `advanced.array_exercises`
CROSS JOIN UNNEST(actors)
```

#### 3) array_exercises 테이블에서 각 영화(title)별로 배우(actor), 배역(character), 장르(genre)를 출력하세요. 한 Row에 배우, 배역, 장르가 모두 표시되어야 합니다
```
SELECT
  title,
  actor,
  character,
  genre
FROM `advanced.array_exercises`
CROSS JOIN UNNEST(actors)
CROSS JOIN UNNEST(genres) AS genre
```

#### 4) 앱 로그 데이터(app_logs)의 배열을 풀어주세요
```
SELECT
  user_id,
  event_date,
  event_name,
  user_pseudo_id,
  params.key,
  params.value.string_value,
  params.value.int_value
FROM `advanced.app_logs_temp`
CROSS JOIN UNNEST(event_params) AS params
WHERE event_date = '2022-08-01'
```

