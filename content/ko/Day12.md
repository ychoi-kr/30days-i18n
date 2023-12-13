# st.checkbox

`st.checkbox`는 체크박스 위젯을 표시합니다.

## 데모 앱

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.checkbox/)

## 코드
`st.checkbox` 사용 방법은 다음과 같습니다:
```python
import streamlit as st

st.header('st.checkbox')

st.write ('주문하고 싶은 것이 무엇인가요?')

icecream = st.checkbox('아이스크림')
coffee = st.checkbox('커피')
cola = st.checkbox('콜라')

if icecream:
     st.write("좋아요! 여기 더 많은 🍦")
    
if coffee: 
     st.write("알겠습니다, 여기 커피 있어요 ☕")

if cola:
     st.write("여기 있어요 🥤")
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
```

이는 앱에 대한 헤더 텍스트를 만드는 것으로 이어집니다:
```python
st.header('st.checkbox')
```

다음으로, `st.write`를 통해 질문을 할 것입니다:
```python
st.write ('주문하고 싶은 것이 무엇인가요?')
```

그 다음으로, 선택할 수 있는 메뉴 항목들을 제공합니다:
```python
icecream = st.checkbox('아이스크림')
coffee = st.checkbox('커피')
cola = st.checkbox('콜라')
```

마지막으로, 어떤 체크박스가 선택되었는지에 따라 맞춤형 텍스트를 출력합니다:
```python
if icecream:
     st.write("좋아요! 여기 더 많은 🍦")
    
if coffee: 
     st.write("알겠습니다, 여기 커피 있어요 ☕")

if cola:
     st.write("여기 있어요 🥤")
```  

## 추가 정보
- [`st.checkbox`](https://docs.streamlit.io/library/api-reference/widgets/st.checkbox)
