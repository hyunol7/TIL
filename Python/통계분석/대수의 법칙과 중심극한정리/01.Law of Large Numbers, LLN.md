대수의 법칙 
===

#### 대수의 법칙
+ 표본의 크기가 커질수록 우리가 얻은 표본 평균이 실제 모집단의 평균에 가까워진다는 원리이다.
  + "많이 해보면 진짜 평균에 가까워진다"

+ Ex > 공정한 동전을 던질 때(앞 면이 나올 확률 0.5, 뒷 면이 나올 확률 0.5)
  + 몇 번 안 던졌을 때 : 10번 던졌는데 앞면이 7번 나왔으면, 표본 평균은 0.7이다, 실제 모평균 0.5와 차이가 있다
  + 아주 많이 던졌을 때 : 만약 10,000번을 던진다면, 앞면이 나온 횟수는 5,000번에 매우 가까워질 것이고, 표본 평균도 0.5에 근접하게 될 것이다.

#### 이것이 바로 대수법칙
+ 시행 횟수가 많아질수록 결과의 불확실성이 줄어들고, 우리가 관찰한 값이 실제 값에 수렴하는 현상을 설명

------

#### 코드
+ 앞면을 1, 뒷면을 0으로 가정하고, 시행 횟수를 늘려가면서 앞면이 나올 확률(표본 평균)이 실제 확률(모평균) 0.5에 어떻게 수렴하는지 관찰
```
import numpy as np
from scipy import stats
import plotly.express as px
import pandas as pd

# 모평균 (공정한 동전의 경우 앞면이 나올 확률)
true_probability = 0.5

# 시뮬레이션할 최대 던지기 횟수
max_trials = 5000

# 각 시행 횟수마다의 표본 평균을 저장할 리스트
sample_means = []

# 시행 횟수를 1부터 max_trials까지 늘려가며 시뮬레이션
for n_trials in range(1, max_trials + 1):
    # 동전 던지기 시뮬레이션 (0: 뒷면, 1: 앞면)
    # np.random.binomial(1, p, size)는 한 번의 시도에서 성공 확률이 p인 베르누이 시행을 size만큼 반복
    trials = np.random.binomial(1, true_probability, n_trials)
    # trials = stats.binom.rvs(1, true_probability, size=n_trials)
    current_mean = np.mean(trials)
    sample_means.append(current_mean)

# 시각화를 위한 데이터프레임 생성
df_lln = pd.DataFrame({
    'Number of Trials': list(range(1, max_trials + 1)),
    'Sample Mean': sample_means
})
df_lln.head()
```
![image](https://github.com/user-attachments/assets/aea7d0b4-250f-4681-a1f5-1495a4cc8a42)

```
# Plotly Express를 사용하여 시각화
fig_lln = px.line(df_lln, x='Number of Trials', y='Sample Mean',
                  title=f'대수의 법칙 시뮬레이션: 동전 던지기 (모평균={true_probability})',
                  labels={'Number of Trials': '던진 횟수', 'Sample Mean': '앞면 비율의 누적 평균'})

# 모평균을 나타내는 수평선 추가
fig_lln.add_hline(y=true_probability, line_dash="dash", line_color="red",
                  annotation_text=f"모평균 = {true_probability}",
                  annotation_position="bottom right")

fig_lln.show()
```
![image](https://github.com/user-attachments/assets/ab244b67-054c-45c8-aa0b-82572c328b38)

#### 던진 횟수가 적을 때는 표본 평균이 0.5 주변에서 크게 변동하지만, 던진 횟수가 점점 많아질수록 표본 평균이 모평균인 0.5에 점점 더 가까워지며 안정되는 것을 확인할 수 있다.

