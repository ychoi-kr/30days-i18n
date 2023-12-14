# st.experimental_get_query_params

`st.experimental_get_query_params`는 사용자 브라우저의 URL에서 직접 쿼리 매개변수를 검색할 수 있게 해줍니다.

## 데모 앱

1. 다음 링크는 쿼리 매개변수가 없는 데모 앱을 로드합니다 (오류 메시지 주목):

[![Streamlit 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.experimental_get_query_params/)

2. 다음 링크는 쿼리 매개변수가 있는 데모 앱을 로드합니다 (여기서는 오류 메시지 없음):

[![Streamlit 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/?firstname=Jack&surname=Beanstalk)

## 코드
`st.experimental_get_query_params`를 사용하는 방법은 다음과 같습니다:
```python
import streamlit as st

st.title('st.experimental_get_query_params')

with st.expander('이 앱에 대하여'):
  st.write("`st.experimental_get_query_params`는 사용자 브라우저의 URL에서 직접 쿼리 매개변수를 검색할 수 있게 해줍니다.")

# 1. 지침
st.header('1. 지침')
st.markdown('''
인터넷 브라우저의 URL 바에서 다음을 추가하세요:
`?firstname=Jack&surname=Beanstalk`
기본 URL `http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/` 뒤에 추가하여
`http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/?firstname=Jack&surname=Beanstalk`가 되도록 합니다.
''')


# 2. st.experimental_get_query_params의 내용
st.header('2. st.experimental_get_query_params의 내용')
st.write(st.experimental_get_query_params())


# 3. URL에서 정보 검색 및 표시
st.header('3. URL에서 정보 검색 및 표시')

firstname = st.experimental_get_query_params()['firstname'][0]
surname = st.experimental_get_query_params()['surname'][0]

st.write(f'안녕하세요 **{firstname} {surname}**, 어떠세요?')
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 임포트하는 것입니다:
```python
import streamlit as st
```

다음으로, 앱에 대한 제목을 설정합니다:
```python
st.title('st.experimental_get_query_params')
```

앱에 대한 설명을 포함하는 드롭다운 박스도 추가합니다:
```python
with st.expander('이 앱에 대하여'):
  st.write("`st.experimental_get_query_params`는 사용자 브라우저의 URL에서 직접 쿼리 매개변수를 검색할 수 있게 해줍니다.")
```

그 다음, 앱 방문자들이 URL에 직접 쿼리 매개변수를 전달하는 방법에 대한 지침을 제공합니다:
```python
# 1. 지침
st.header('1. 지침')
st.markdown('''
인터넷 브라우저의 URL 바에서 다음을 추가하세요:
`?firstname=Jack&surname=Beanstalk`
기본 URL `http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/` 뒤에 추가하여
`http://share.streamlit.io/dataprofessor/st.experimental_get_query_params/?firstname=Jack&surname=Beanstalk`가 되도록 합니다.
''')
```

그 후, `st.experimental_get_query_params` 명령의 내용을 표시합니다.
```python
# 2. st.experimental_get_query_params의 내용
st.header('2. st.experimental_get_query_params의 내용')
st.write(st.experimental_get_query_params())
```

마지막으로, URL의 쿼리 매개변수에서 선택적 정보를 추출하여 표시합니다

:
```python
# 3. URL에서 정보 검색 및 표시
st.header('3. URL에서 정보 검색 및 표시')

firstname = st.experimental_get_query_params()['firstname'][0]
surname = st.experimental_get_query_params()['surname'][0]

st.write(f'안녕하세요 **{firstname} {surname}**, 어떠세요?')
```

## 추가 읽기
- [`st.experimental_get_query_params`](https://docs.streamlit.io/library/api-reference/utilities/st.experimental_get_query_params)
