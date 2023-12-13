# st.selectbox

`st.selectbox`는 선택 위젯을 표시할 수 있게 합니다.

## 우리가 만드는 것은?

사용자에게 가장 좋아하는 색상이 무엇인지 묻는 간단한 앱입니다.

앱의 흐름:
1. 사용자가 색상을 선택합니다.
2. 앱이 선택된 색상을 출력합니다.

## 데모 앱
배포된 Streamlit 앱은 아래 링크에 표시된 것과 같아야 합니다:

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.selectbox/)

## 코드
위에서 언급한 앱을 구현하기 위한 코드는 다음과 같습니다:
```python
import streamlit as st

st.header('st.selectbox')

option = st.selectbox(
     '가장 좋아하는 색상은 무엇인가요?',
     ('파랑', '빨강', '초록'))

st.write('당신이 좋아하는 색상은 ', option)
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
```

이는 앱에 대한 헤더 텍스트를 만드는 것으로 이어집니다:
```python
st.header('st.selectbox')
```

다음으로, `option`이라는 변수를 생성하고 `st.selectbox()` 명령어를 통해 **선택** 입력 위젯 형태로 사용자 입력을 받습니다.

```python
option = st.selectbox(
     '가장 좋아하는 색상은 무엇인가요?',
     ('파랑', '빨강', '초록'))
```
위 코드 상자에서 볼 수 있듯이, `st.selectbox()` 명령어는 2개의 입력 인수를 받습니다:
1. 선택 위젯 위에 표시되는 텍스트, 즉 `'가장 좋아하는 색상은 무엇인가요?'`
2. 선택할 수 있는 가능한 값들 `('파랑', '빨강', '초록')`

마지막으로, 선택된 색상을 다음과 같이 출력합니다:
```python
st.write('당신이 좋아하는 색상은 ', option)
```

## 다음 단계
지금까지 Streamlit 앱을 로컬에서 생성했다면, 이제 [Streamlit Community Cloud](https://streamlit.io/cloud)에 배포할 시간입니다.

## 참고 자료
[`st.selectbox`](https://docs.streamlit.io/library/api-reference/widgets/st.selectbox)에 대해 더 알아보세요.
