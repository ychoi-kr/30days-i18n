# Bored API 앱 사용 방법

Bored API 앱은 당신이 지루할 때 할 수 있는 재미있는 활동을 제안합니다!

기술적으로, 이 앱은 Streamlit 앱 내에서 API를 사용하는 방법을 시연합니다.

## 데모 앱

[![Streamlit 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/bored-api-app/)

## 코드
Bored-API 앱을 구현하는 방법은 다음과 같습니다:
```python
import streamlit as st
import requests

st.title('🏀 Bored API 앱')

st.sidebar.header('입력')
selected_type = st.sidebar.selectbox('활동 유형 선택', ["education", "recreational", "social", "diy", "charity", "cooking", "relaxation", "music", "busywork"])

suggested_activity_url = f'http://www.boredapi.com/api/activity?type={selected_type}'
json_data = requests.get(suggested_activity_url)
suggested_activity = json_data.json()

c1, c2 = st.columns(2)
with c1:
  with st.expander('이 앱에 대하여'):
    st.write('지루하신가요? **Bored API 앱**은 지루할 때 할 수 있는 활동을 제안합니다. 이 앱은 Bored API에 의해 구동됩니다.')
with c2:
  with st.expander('JSON 데이터'):
    st.write(suggested_activity)
    
st.header('제안된 활동')
st.info(suggested_activity['activity'])

col1, col2, col3 = st.columns(3)
with col1:
  st.metric(label='참가자 수', value=suggested_activity['participants'], delta='')
with col2:
  st.metric(label='활동 유형', value=suggested_activity['type'].capitalize(), delta='')
with col3:
  st.metric(label='가격', value=suggested_activity['price'], delta='')
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 할 일은 다음과 같이 `streamlit` 라이브러리와 `requests` 라이브러리를 임포트하는 것입니다:
```python
import streamlit as st
import requests
```

앱의 제목은 `st.title`을 통해 표시됩니다:
```python
st.title('🏀 Bored API 앱')
```

다음으로, `st.selectbox` 명령을 통해 사용자로부터 **활동 유형**에 대한 입력을 받습니다:
```python
st.sidebar.header('입력')
selected_type = st.sidebar.selectbox('활동 유형 선택', ["education", "recreational", "social", "diy", "charity", "cooking", "relaxation", "music", "busywork"])
```

위에서 언급한 선택된 활동은 f-string을 통해 URL에 추가되며, 이를 사용하여 결과 JSON 데이터를 검색합니다: 
```python
suggested_activity_url = f'http://www.boredapi.com/api/activity?type={selected_type}'
json_data = requests.get(suggested_activity_url)
suggested_activity = json_data.json()
```

여기서는 `st.expander` 명령을 통해 앱에 대한 정보와 JSON 데이터를 표시합니다.
```python
c1, c2 = st.columns(2)
with c1:
  with st.expander('이 앱에 대하여'):
    st.write('지루하신가요? **Bored API 앱**은 지루할 때 할 수 있는 활동을 제안합니다. 이 앱은 Bored API에 의해 구동됩니다.')
with c2:
  with st.expander('JSON 데이터'):
    st.write(suggested_activity)
```

그런 다음 제안된 활동을 다음과 같이 표시합니다:
```python
st.header('제안된 활동')
st.info(suggested_activity['activity'])
```

마지막으로, 제안된 활동의 `참가자 수`, `활동 유형`, `가격`과 같은 정보를 표시합니다.
```python
col1, col2, col3 = st.columns

(3)
with col1:
  st.metric(label='참가자 수', value=suggested_activity['participants'], delta='')
with col2:
  st.metric(label='활동 유형', value=suggested_activity['type'].capitalize(), delta='')
with col3:
  st.metric(label='가격', value=suggested_activity['price'], delta='')
```

## 추가 읽기
- [Bored API](http://www.boredapi.com/)
