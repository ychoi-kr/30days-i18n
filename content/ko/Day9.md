# st.line_chart

`st.line_chart`는 라인 차트를 표시합니다.

이 명령어는 `st.altair_chart` 주위의 구문 설탕이며, 주요 차이점은 데이터의 자체 열과 인덱스를 사용하여 차트의 사양을 파악하는 것입니다. 결과적으로 많은 "그냥 이것을 그래프로 그리세요" 시나리오에서 사용하기 쉬우면서도, 사용자 정의가 덜 가능합니다.

`st.line_chart`가 데이터 사양을 올바르게 추측하지 못하면, 원하는 차트를 st.altair_chart를 사용하여 지정해 보세요.

## 우리가 만드는 것은?

라인 차트를 표시하는 간단한 앱입니다.

앱의 흐름:
1. `NumPy`를 통해 무작위로 생성된 숫자로부터 `Pandas` 데이터프레임을 생성합니다.
2. `st.line_chart()` 명령을 사용하여 라인 차트를 생성하고 표시합니다.

## 데모 앱

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.line_chart/)

## 코드
[`st.line_chart`](https://docs.streamlit.io/library/api-reference/charts/st.line_chart) 사용 방법은 다음과 같습니다:
```python
import streamlit as st
import pandas as pd
import numpy as np

st.header('라인 차트')

chart_data = pd.DataFrame(
     np.random.randn(20, 3),
     columns=['a', 'b', 'c'])

st.line_chart(chart_data)

```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오고 다른 라이브러리들을 가져오는 것입니다:
```python
import streamlit as st
import pandas as pd
import numpy as np
```

다음으로, 앱의 헤더 텍스트를 생성합니다:
```python
st.header('라인 차트')
```

그 후, 3개의 열을 포함하는 무작위로 생성된 숫자들로 데이터프레임을 생성합니다.
```python
chart_data = pd.DataFrame(
     np.random.randn(20, 3),
     columns=['a', 'b', 'c'])
```

마지막으로, `st.line_chart()`를 사용하여 `chart_data` 변수에 저장된 데이터프레임을 입력 데이터로 사용하여 라인 차트를 생성합니다:
```python
st.line_chart(chart_data)
```

## 추가 정보
[`st.line_chart`](https://docs.streamlit.io/library/api-reference/charts/st.line_chart)가 기반으로 하는 다음과 관련된 Streamlit 명령어에 대해 자세히 알아보세요:
- [`st.altair_chart`](https://docs.streamlit.io/library/api-reference/charts/st.altair_chart)
