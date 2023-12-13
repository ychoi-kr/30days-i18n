# `st.write`란?

`st.write`는 스트림릿 앱에 텍스트와 인수를 작성하는 데 사용됩니다.

텍스트를 표시할 수 있을 뿐만 아니라, `st.write()` 명령을 통해 다음도 표시할 수 있습니다:


- 문자열 출력; `st.markdown()`처럼 작동
- 파이썬 `dict` 표시
- `pandas` DataFrame을 테이블로 표시
- `matplotlib`, `plotly`, `altair`, `graphviz`, `bokeh`의 플롯/그래프/그림
- 그 외 더 많음 ([st.write API 문서 참조](https://docs.streamlit.io/library/api-reference/write-magic/st.write))

## 무엇을 만들고 있나요?

텍스트, 숫자, DataFrames, 그래프 등을 표시하는 방법에 대해 다양한 예제를 보여주는 간단한 앱입니다.

## 데모 앱

배포된 스트림릿 앱은 아래 링크에 있는 것과 비슷하게 보일 것입니다:

[![스트림릿 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.write/)

## 코드

`st.write` 사용 방법은 다음과 같습니다:

```python
import numpy as np
import altair as alt
import pandas as pd
import streamlit as st

st.header('st.write')

# 예제 1

st.write('안녕하세요, *세계여!* :sunglasses:')

# 예제 2

st.write(1234)

# 예제 3

df = pd.DataFrame({
     '첫 번째 컬럼': [1, 2, 3, 4],
     '두 번째 컬럼': [10, 20, 30, 40]
     })
st.write(df)

# 예제 4

st.write('아래는 DataFrame입니다:', df, '위는 dataframe입니다.')

# 예제 5

df2 = pd.DataFrame(
     np.random.randn(200, 3),
     columns=['a', 'b', 'c'])
c = alt.Chart(df2).mark_circle().encode(
     x='a', y='b', size='c', color='c', tooltip=['a', 'b', 'c'])
st.write(c)
```

## 한 줄씩 설명

스트림릿 앱을 만들 때 가장 먼저 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:

```python
import streamlit as st
```

이어서 앱에 대한 헤더 텍스트를 생성합니다:

```python
st.header('st.write')
```

**예제 1**
기본적인 사용법은 텍스트와 마크다운 형식의 텍스트를 표시하는 것입니다:

```python
st.write('안녕하세요, *세계여!* :sunglasses:')
```

**예제 2**
앞서 언급했듯이, 숫자와 같은 다른 데이터 형식도 표시할 수 있습니다:

```python
st.write(1234)
```

**예제 3**
DataFrame도 다음과 같이 표시할 수 있습니다:

```python
df = pd.DataFrame({
     '첫 번째 컬럼': [1, 2, 3, 4],
     '두 번째 컬럼': [10, 20, 30, 40]
     })
st.write(df)
```

**예제 4**
여러 인수를 전달할 수 있습니다:

```python
st.write('아래는 DataFrame입니다:', df, '위는 dataframe입니다.')
```

**예제 5**
마지막으로, 변수로 전달함으로써 그래프도 표시할 수 있습니다:

```python
df2 = pd.DataFrame(
     np.random.randn(200, 3),
     columns=['a', 'b', 'c'])
c = alt.Chart(df2).mark_circle().encode(
     x='a', y='b', size='c', color='c', tooltip=['a', 'b', 'c'])
st.write(c)
```

## 데모 앱

배포된 스트림릿 앱은 아래 링크에 있는 것과 비슷하게 보일 것입니다:

[![스트림릿 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.write/)

## 다음 단계

이제 로컬에서 스트림릿 앱을 만들었으니, 곧 다가올 챌린지에서 [스트림릿 커뮤니티 클라우드](https://streamlit.io/cloud)에 배포하는 방법을 설명할 것입니다.

이것이 당신의 첫 번째 챌린지 주이므로, 우리는 전체 코드(위 코드 상자에 표시된 것과 같은)와 솔루션(데모 앱)을 이 웹페이지 안에 바로 제공합니다.

다음 챌린지에서는 먼저 스트림릿 앱을 직접 구현하는 것이 권장됩니다.

만약 막히게 되면, 언제든지 해결책을 엿볼 수 있습니다.

## 추가 읽기

[`st.write`](https://

docs.streamlit.io/library/api-reference/write-magic/st.write) 외에도, 다른 방법으로 텍스트를 표시하는 방법을 탐색할 수 있습니다:

- [`st.markdown`](https://docs.streamlit.io/library/api-reference/text/st.markdown)
- [`st.header`](https://docs.streamlit.io/library/api-reference/text/st.header)
- [`st.subheader`](https://docs.streamlit.io/library/api-reference/text/st.subheader)
- [`st.caption`](https://docs.streamlit.io/library/api-reference/text/st.caption)
- [`st.text`](https://docs.streamlit.io/library/api-reference/text/st.text)
- [`st.latex`](https://docs.streamlit.io/library/api-reference/text/st.latex)
- [`st.code`](https://docs.streamlit.io/library/api-reference/text/st.code)
