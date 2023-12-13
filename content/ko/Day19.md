# Streamlit 앱 레이아웃 구성하기

이 튜토리얼에서는 다음 명령어를 사용하여 Streamlit 앱의 레이아웃을 구성합니다:
- `st.set_page_config(layout="wide")` - 앱의 내용을 넓은 모드로 표시합니다 (기본적으로 내용은 고정된 너비의 박스에 포함됩니다).
- `st.sidebar` - 위젯이나 텍스트/이미지 디스플레이를 사이드바에 배치합니다.
- `st.expander` - 텍스트/이미지 디스플레이를 접을 수 있는 컨테이너 박스 내에 배치합니다.
- `st.columns` - 컨텐츠를 내부에 배치할 수 있는 표 형태의 공간(또는 열)을 생성합니다.

## 데모 앱

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/streamlit-layout/)

## 코드
Streamlit 앱의 레이아웃을 사용자 정의하는 방법은 다음과 같습니다:
```python
import streamlit as st

st.set_page_config(layout="wide")

st.title('Streamlit 앱 레이아웃 구성하기')

with st.expander('이 앱에 대하여'):
  st.write('이 앱은 Streamlit 앱을 구성하는 다양한 방법을 보여줍니다.')
  st.image('https://streamlit.io/images/brand/streamlit-logo-secondary-colormark-darktext.png', width=250)

st.sidebar.header('입력')
user_name = st.sidebar.text_input('당신의 이름은 무엇인가요?')
user_emoji = st.sidebar.selectbox('이모티콘 선택', ['', '😄', '😆', '😊', '😍', '😴', '😕', '😱'])
user_food = st.sidebar.selectbox('가장 좋아하는 음식은?', ['', 'Tom Yum Kung', 'Burrito', 'Lasagna', 'Hamburger', 'Pizza'])

st.header('출력')

col1, col2, col3 = st.columns(3)

with col1:
  if user_name != '':
    st.write(f'👋 안녕하세요 {user_name}님!')
  else:
    st.write('👈  **이름**을 입력해 주세요!')

with col2:
  if user_emoji != '':
    st.write(f'{user_emoji}는 당신이 좋아하는 **이모티콘**입니다!')
  else:
    st.write('👈 **이모티콘**을 선택해 주세요!')

with col3:
  if user_food != '':
    st.write(f'🍴 **{user_food}**은 당신이 좋아하는 **음식**입니다!')
  else:
    st.write('👈 가장 좋아하는 **음식**을 선택해 주세요!')
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
```

우선 페이지 레이아웃을 `wide` 모드로 정의하여 페이지 콘텐츠가 브라우저의 너비로 확장되도록 합니다.
```python
st.set_page_config(layout="wide")
```

다음으로, Streamlit 앱에 제목을 부여합니다.
```python
st.title('Streamlit 앱 레이아웃 구성하기')
```

앱 제목 아래에 `이 앱에 대하여`라는 제목의 확장 가능한 상자를 배치합니다. 확장 시 내부에서 추가 세부 정보를 볼 수 있습니다.
```python
with st.expander('이 앱에 대하여'):
  st.write('이 앱은 Streamlit 앱을 구성하는 다양한 방법을 보여줍니다.')
  st.image('https://streamlit.io/images/brand/streamlit-logo-secondary-colormark-darktext.png', width=250)
```

사용자 입력을 받기 위한 입력 위젯은 `st.sidebar` 명령어를 사용하여 사이드바에 배치됩니다. 사용자가 입력하거나 선택한 입력값은 `user_name`, `user_emoji`, `user_food` 변수에 할당되어 저장됩니다.
```python
st.sidebar.header('입력')
user_name = st.sidebar.text_input('당신의 이름은 무엇인가요?')
user_emoji = st.sidebar.selectbox('이모티콘 선택', ['', '😄', '😆', '😊', '😍', '😴', '😕', '😱'])
user_food = st.sidebar.selectbox('가장 좋아하는 음식은?', ['', 'Tom Yum Kung', 'Burrito', 'Lasagna', 'Hamburger', 'Pizza'])
```

마지막으로, `st.columns` 명령어를 사용하여 `col1`, `col2`, `col3`에 해당하는 3개의 열을 생성합니다. 그런 다음, 각 열에 내용을 배치하기 위해 `with` 문으로 시작하는 개별 코드 블록을 생성합니다. 이 하에 사용자가 사이드바에서 제공한 입력 데이터를 제공했는지 여부에 따라 2가지 대체 텍스트 중 하나를 표시하는 조건문을 생성합니다. 기본적으로 페이지는 `else` 문 아래의 텍스트를 표시합니다. 사용자가 입력을 제공하면 `Output` 헤더 텍스트 아래에 앱에 제공한 사용자 정보가 표시됩니다.
```python
st.header('출력')

col1, col2, col3 = st.columns(3)

with col1:
  if user_name != '':
    st.write(f'👋 안녕하세요 {user_name}님!')
  else:
    st.write('👈  **이름**을 입력해 주세요!')

with col2:
  if user_emoji != '':
    st.write(f'{user_emoji}는 당신이

 좋아하는 **이모티콘**입니다!')
  else:
    st.write('👈 **이모티콘**을 선택해 주세요!')

with col3:
  if user_food != '':
    st.write(f'🍴 **{user_food}**은 당신이 좋아하는 **음식**입니다!')
  else:
    st.write('👈 가장 좋아하는 **음식**을 선택해 주세요!')
```
사용자가 제공한 값과 미리 준비된 텍스트를 함께 결합하기 위해 `f` 문자열을 사용했다는 점을 언급할 가치가 있습니다.

## 추가 정보
- [레이아웃 및 컨테이너](https://docs.streamlit.io/library/api-reference/layout)
