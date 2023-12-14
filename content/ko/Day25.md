# st.session_state

브라우저 탭에서의 Streamlit 앱 접속을 세션으로 정의합니다. Streamlit 서버에 연결하는 각 브라우저 탭마다 새로운 세션이 생성됩니다. 앱과 상호작용할 때마다 Streamlit은 스크립트를 처음부터 다시 실행합니다. 각 재실행은 백지 상태에서 이루어집니다: 재실행 간에 변수들이 공유되지 않습니다.

세션 상태는 각 사용자 세션 간에 변수를 공유하는 방법입니다. 상태를 저장하고 유지하는 능력 외에도, Streamlit은 콜백을 사용하여 상태를 조작할 수 있는 기능을 제공합니다.

이 튜토리얼에서는 체중 변환 앱을 만들면서 세션 상태와 콜백의 사용법을 설명하겠습니다.

`st.session_state`는 Streamlit 앱에서 세션 상태를 구현할 수 있게 해줍니다.

## 데모 앱

[![Streamlit 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.session_state/)

## 코드
`st.session_state`를 사용하는 방법은 다음과 같습니다:
```python
import streamlit as st

st.title('st.session_state')

def lbs_to_kg():
  st.session_state.kg = st.session_state.lbs/2.2046
def kg_to_lbs():
  st.session_state.lbs = st.session_state.kg*2.2046

st.header('입력')
col1, spacer, col2 = st.columns([2,1,2])
with col1:
  pounds = st.number_input("파운드:", key = "lbs", on_change = lbs_to_kg)
with col2:
  kilogram = st.number_input("킬로그램:", key = "kg", on_change = kg_to_lbs)

st.header('출력')
st.write("st.session_state 객체:", st.session_state)
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 임포트하는 것입니다:
```python
import streamlit as st
```

먼저, 앱의 제목을 만듭니다:
```python
st.title('st.session_state')
```

그 다음, 파운드에서 킬로그램으로, 그 반대로 체중을 변환하는 사용자 정의 함수를 정의합니다:
```python
def lbs_to_kg():
  st.session_state.kg = st.session_state.lbs/2.2046
def kg_to_lbs():
  st.session_state.lbs = st.session_state.kg*2.2046
```

여기서는 `st.number_input`을 사용하여 체중 값을 숫자로 입력받습니다:
```python
st.header('입력')
col1, spacer, col2 = st.columns([2,1,2])
with col1:
  pounds = st.number_input("파운드:", key = "lbs", on_change = lbs_to_kg)
with col2:
  kilogram = st.number_input("킬로그램:", key = "kg", on_change = kg_to_lbs)
```
위의 두 사용자 정의 함수는 `st.number_input` 명령으로 생성된 숫자 상자에 숫자가 입력되자마자 호출됩니다. `on_change` 옵션에는 `lbs_to_kg` 및 `kg_to_lbs` 두 사용자 정의 함수가 지정됩니다.

간단히 말해서, `st.number_input` 상자에 숫자를 입력하면 이 사용자 정의 함수들에 의해 숫자가 변환됩니다.

마지막으로, 세션 상태에 저장된 `kg` 및 `lbs` 단위의 체중 값이 `st.session_state.kg` 및 `st.session_state.lbs`로 `st.write`를 통해 출력됩니다:
```python
st.header('출력')
st.write("st.session_state 객체:", st.session_state)
```

## 추가 읽기
- [세션 상태](https://docs.streamlit.io/library/api-reference/session-state)
- [앱에 상태 추가](https://docs.streamlit.io/library/advanced-features/session-state)
