# st.progress

`st.progress`는 반복이 진행됨에 따라 그래픽으로 업데이트되는 진행률 표시줄을 보여줍니다.

## 데모 앱

[![Streamlit 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.progress/)

## 코드
`st.progress`를 사용하는 방법은 다음과 같습니다:
```python
import streamlit as st
import time

st.title('st.progress')

with st.expander('이 앱에 대하여'):
     st.write('`st.progress` 명령어를 사용하여 Streamlit 앱에서 계산의 진행 상태를 표시할 수 있습니다.')

my_bar = st.progress(0)

for percent_complete in range(100):
     time.sleep(0.05)
     my_bar.progress(percent_complete + 1)

st.balloons()
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 할 일은 `streamlit` 라이브러리를 `st`로 임포트하고 `time` 라이브러리도 임포트하는 것입니다:
```python
import streamlit as st
import time
```

다음으로, 앱에 대한 제목 텍스트를 생성합니다:
```python
st.title('st.progress')
```

`st.expander`를 사용하여 **앱 정보 상자**를 만들고 `st.write`를 통해 설명을 표시합니다:
```python
with st.expander('이 앱에 대하여'):
     st.write('`st.progress` 명령어를 사용하여 Streamlit 앱에서 계산의 진행 상태를 표시할 수 있습니다.')
```

마지막으로, 진행률 표시줄을 정의하고 `0`으로 시작값을 설정합니다. 그런 다음 `for` 루프가 `0`부터 `100`까지 반복합니다. 각 반복마다 `time.sleep(0.05)`를 사용하여 앱이 `0.05초` 동안 대기한 후에 `my_bar` 진행률 표시줄에 `1`을 추가합니다. 이렇게 하면 각 반복마다 표시줄의 그래픽 표시가 증가합니다.
```python
my_bar = st.progress(0)

for percent_complete in range(100):
     time.sleep(0.05)
     my_bar.progress(percent_complete + 1)

st.balloons()
```

## 추가 읽기
- [`st.progress`](https://docs.streamlit.io/library/api-reference/status/st.progress)
