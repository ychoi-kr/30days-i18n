# st.slider

`st.slider`는 슬라이더 입력 위젯을 표시합니다.

지원되는 데이터 유형은 int, float, date, time 및 datetime입니다.

## 우리가 만드는 것은?

슬라이더 위젯을 조정하여 사용자 입력을 받는 다양한 방법을 보여주는 간단한 앱입니다.

앱의 흐름:
1. 사용자가 슬라이더 위젯을 조정하여 값을 선택합니다.
2. 앱이 선택된 값을 출력합니다.

## 데모 앱

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.slider/)

## 코드
st.slider 사용 방법은 다음과 같습니다:

```python
import streamlit as st
from datetime import time, datetime

st.header('st.slider')

# 예제 1

st.subheader('Slider')

age = st.slider('당신의 나이는?', 0, 130, 25)
st.write("나는 ", age, '살입니다')

# 예제 2

st.subheader('범위 슬라이더')

values = st.slider(
     '값의 범위를 선택하세요',
     0.0, 100.0, (25.0, 75.0))
st.write('값:', values)

# 예제 3

st.subheader('시간 범위 슬라이더')

appointment = st.slider(
     "약속을 예약하세요:",
     value=(time(11, 30), time(12, 45)))
st.write("예약된 시간:", appointment)

# 예제 4

st.subheader('날짜 및 시간 슬라이더')

start_time = st.slider(
     "언제 시작하시겠습니까?",
     value=datetime(2020, 1, 1, 9, 30),
     format="MM/DD/YY - hh:mm")
st.write("시작 시간:", start_time)

```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
from datetime import time, datetime
```

이는 앱에 대한 헤더 텍스트를 만드는 것으로 이어집니다:
```python
st.header('st.slider')
```

**예제 1**

슬라이더:

```python
st.subheader('Slider')

age = st.slider('당신의 나이는?', 0, 130, 25)
st.write("나는 ", age, '살입니다')
```

여기에서 `st.slider()` 명령어는 사용자의 나이에 대한 입력을 수집하는 데 사용됩니다.

첫 번째 입력 인수는 슬라이더 위젯 바로 위에 표시되는 텍스트로 `'당신의 나이는?'`을 묻습니다.

다음 세 정수 `0, 130, 25`는 각각 최소값, 최대값 및 기본값을 나타냅니다.

**예제 2**

범위 슬라이더:

```python
st.subheader('범위 슬라이더')

values = st.slider(
     '값의 범위를 선택하세요',
     0.0, 100.0, (25.0, 75.0))
st.write('값:', values)
```

범위 슬라이더는 하한 및 상한 값 쌍을 선택할 수 있게 합니다.

첫 번째 입력 인수는 범위 슬라이더 위젯 바로 위에 표시되는 텍스트로 `'값의 범위를 선택하세요'`를 묻습니다.

다음 세 인수 `0.0, 100.0, (25.0, 75.0)`는 최소값과 최대값을 나타내며, 마지막 튜플은 하한(25.0) 및 상한(75.0) 값으로 사용할 기본값을 나타냅니다.

**예제 3**

시간 범위 슬라이더:

```python
st.subheader('시간 범위 슬라이더')

appointment = st.slider(
     "약속을 예약하세요:",
     value=(time(11, 30), time(12, 45)))
st.write("예약된 시간:", appointment)
```

시간 범위 슬라이더는 날짜 및 시간의 하한 및 상한 값 쌍을 선택할 수 있게 합니다.

첫 번째 입력 인수는 시간 범위 슬라이더 위젯 바로 위에 표시되는 텍스트로 `'약속을 예약하세요:'`를 묻습니다.

하한 및 상한 시간 쌍의 기본값은 각각 11:30과 12:45로 설정됩니다.

**예제 4**

날짜 및 시간 슬라이더:

```python
st.subheader('날짜 및 시간 슬라이더')

start_time = st.slider(
     "언제 시작하시겠습니까?",
     value=datetime(2020, 1, 1, 9, 30),
     format="MM/DD/YY - hh:mm")
st.write("시작 시간:", start_time)
```

날짜 및 시간 슬라이더는 날짜 및 시간을 선택할 수 있게 합니다.

첫 번째 입력 인수는 날짜 및 시간 슬라이더 위젯 바로 위에 표시되는 텍스트로 `'언제 시작하시겠습니까?'`를 묻습니다.

날짜 및 시간의 기본값은 `value` 옵션을 사용하여 2020년 1월 1일 오전 9시 30분으로 설정되었습니다.

## 추가 정보
다음과 관련된 위젯도 탐색해 볼 수 있습니다:
- [`st.select_slider`](https://docs.streamlit.io/library/api-reference/widgets/st.select_slider)
