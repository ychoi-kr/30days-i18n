# Streamlit 앱의 테마 사용자 정의하기

`.streamlit` 폴더 내의 앱과 동일한 폴더에 저장된 `config.toml`이라는 구성 파일의 매개변수를 조정하여 테마를 사용자 정의할 수 있습니다.

## 우리가 만드는 것은?

테마 사용자 정의의 결과를 보여주는 간단한 앱입니다. 이는 [`.streamlit/config.toml`](https://github.com/dataprofessor/streamlit-custom-theme/blob/master/.streamlit/config.toml) 파일 내의 HTML HEX 코드를 사용자 정의함으로써 가능합니다.

## 데모 앱

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/streamlit-custom-theme/)

## 코드
[`streamlit_app.py`](https://github.com/dataprofessor/streamlit-custom-theme/blob/master/streamlit_app.py) 파일의 코드는 다음과 같습니다:
```python
import streamlit as st

st.title('Streamlit 앱의 테마 사용자 정의하기')

st.write('이 앱의 `.streamlit/config.toml` 파일 내용')

st.code("""
[theme]
primaryColor="#F39C12"
backgroundColor="#2E86C1"
secondaryBackgroundColor="#AED6F1"
textColor="#FFFFFF"
font="monospace"
""")

number = st.sidebar.slider('숫자를 선택하세요:', 0, 10, 5)
st.write('슬라이더 위젯에서 선택된 숫자:', number)
```

[`.streamlit/config.toml`](https://github.com/dataprofessor/streamlit-custom-theme/blob/master/.streamlit/config.toml) 파일의 코드는 다음과 같습니다:
```python
[theme]
primaryColor="#F39C12"
backgroundColor="#2E86C1"
secondaryBackgroundColor="#AED6F1"
textColor="#FFFFFF"
font="monospace"
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
```

이는 앱에 대한 제목 텍스트를 만드는 것으로 이어집니다:
```python
st.title('config.toml을 사용한 테마링')
```

다음으로, `.streamlit/config.toml` 파일의 내용을 표시할 것입니다. 우선 `st.write`를 통해 주의 사항을 표시한 다음 `st.code`를 사용하여 실제 코드를 표시합니다:
```python
st.write('이 앱의 ./streamlit/config.toml 파일 내용')

st.code("""
[theme]
primaryColor="#F39C12"
backgroundColor="#2E86C1"
secondaryBackgroundColor="#AED6F1"
textColor="#FFFFFF"
font="monospace"
""")
```

마지막으로, 사이드바에 슬라이더 위젯을 생성한 후 선택된 숫자를 표시합니다:
```python
number = st.sidebar.slider('숫자를 선택하세요:', 0, 10, 5)
st.write('슬라이더 위젯에서 선택된 숫자:', number)
```

이 앱에서 사용한 맞춤 색상을 살펴보겠습니다. 이는 `.streamlit/config.toml` 파일에 지정되어 있습니다:
- `primaryColor="#F39C12"` - 주 색상을 오렌지색으로 설정합니다. 슬라이더 위젯의 오렌지색을 확인하세요.
- `backgroundColor="#2E86C1"` - 배경색을 파란색으로 설정합니다. 메인 패널의 파란색 배경을 확인하세요.
- `secondaryBackgroundColor="#AED6F1"` - 보조 배경색을 어두운 회색으로 설정합니다. 사이드바의 회색 배경과 메인 패널의 코드 박스 배경색을 확인하세요.
- `textColor="#FFFFFF"` - 텍스트 색상을 흰색으로 설정합니다.
- `font="monospace"` - 폰트를 모노스페이스로 설정합니다.


## 추가 정보
- [테마링](https://docs.streamlit.io/library/advanced-features/theming)
- [HTML 색상 코드](https://htmlcolorcodes.com/)는 관심 있는 색상을 선택하는 데 유용한 도구입니다.
