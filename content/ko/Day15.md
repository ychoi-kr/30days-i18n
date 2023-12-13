# st.latex

`st.latex`는 LaTeX로 서식이 지정된 수학적 표현을 표시합니다.

## 우리가 만드는 것은?

`st.latex` 명령을 사용하여 LaTeX 구문으로 수학 방정식을 표시하는 간단한 앱입니다.

## 데모 앱
[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.latex/)

## 코드
`st.latex` 사용 방법은 다음과 같습니다:
```python
import streamlit as st

st.header('st.latex')

st.latex(r'''
     a + ar + a r^2 + a r^3 + \cdots + a r^{n-1} =
     \sum_{k=0}^{n-1} ar^k =
     a \left(\frac{1-r^{n}}{1-r}\right)
     ''')
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
```

이는 앱에 대한 헤더 텍스트를 만드는 것으로 이어집니다:
```python
st.header('st.latex')
```

다음으로, `st.latex`를 통해 수학 방정식을 표시합니다:
```python
st.latex(r'''
     a + ar + a r^2 + a r^3 + \cdots + a r^{n-1} =
     \sum_{k=0}^{n-1} ar^k =
     a \left(\frac{1-r^{n}}{1-r}\right)
     ''')
```

## 참고 자료
- Streamlit API 문서에서 [`st.latex`](https://docs.streamlit.io/library/api-reference/text/st.latex)에 대해 자세히 알아보세요.
