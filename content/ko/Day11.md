# st.multiselect

`st.multiselect`는 여러 항목을 선택할 수 있는 위젯을 표시합니다.

## 데모 앱

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.multiselect/)

## 코드
`st.multiselect` 사용 방법은 다음과 같습니다:
```python
import streamlit as st

st.header('st.multiselect')

options = st.multiselect(
     '가장 좋아하는 색상은 무엇인가요',
     ['초록', '노랑', '빨강', '파랑'],
     ['노랑', '빨강'])

st.write('당신이 선택한 색상:', options)
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
```

이는 앱에 대한 헤더 텍스트를 만드는 것으로 이어집니다:
```python
st.header('st.multiselect')
```

다음으로, 사용자가 하나 이상의 색상을 선택할 수 있도록 `st.multiselect` 위젯을 사용할 것입니다.

```python
options = st.multiselect(
     '가장 좋아하는 색상은 무엇인가요',
     ['초록', '노랑', '빨강', '파랑'],
     ['노랑', '빨강'])
```

마지막으로, 선택된 색상들을 출력합니다:
```python
st.write('당신이 선택한 색상:', options)
```

## 추가 정보
- [`st.multiselect`](https://docs.streamlit.io/library/api-reference/widgets/st.multiselect)
