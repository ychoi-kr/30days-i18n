# st.file_uploader

`st.file_uploader`는 파일 업로더 위젯을 표시합니다[[1](https://docs.streamlit.io/library/api-reference/widgets/st.file_uploader)].

기본적으로 업로드된 파일은 200MB로 제한됩니다. 이는 `server.maxUploadSize` 구성 옵션을 사용하여 설정할 수 있습니다. 구성 옵션을 설정하는 방법에 대한 자세한 내용은 [[2](https://docs.streamlit.io/library/advanced-features/configuration#set-configuration-options)]에서 확인할 수 있습니다.

## 데모 앱

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.file_uploader/)

## 코드
`st.file_uploader` 사용 방법은 다음과 같습니다:
```python
import streamlit as st
import pandas as pd

st.title('st.file_uploader')

st.subheader('CSV 입력')
uploaded_file = st.file_uploader("파일 선택")

if uploaded_file is not None:
  df = pd.read_csv(uploaded_file)
  st.subheader('DataFrame')
  st.write(df)
  st.subheader('기술 통계')
  st.write(df.describe())
else:
  st.info('☝️ CSV 파일을 업로드하세요')
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오고, 필요한 다른 라이브러리를 가져오는 것입니다:
```python
import streamlit as st
import pandas as pd
```

이는 앱에 대한 제목 텍스트를 만드는 것으로 이어집니다:
```python
st.title('st.file_uploader')
```

다음으로, 사용자 입력 파일을 받기 위해 `st.file_uploader`를 사용하여 파일 업로더 위젯을 표시합니다:
```python
st.subheader('CSV 입력')
uploaded_file = st.file_uploader("파일 선택")
```

마지막으로, 파일을 업로드할 때까지 사용자에게 파일 업로드를 요청하는 환영 메시지를 표시하는 조건문을 정의합니다(`else` 조건에서 구현됨). 파일 업로드 시 `if` 문이 활성화되고 `pandas` 라이브러리를 통해 CSV 파일을 읽고 `st.write` 명령을 통해 표시합니다.
```python
if uploaded_file is not None:
  df = pd.read_csv(uploaded_file)
  st.subheader('DataFrame')
  st.write(df)
  st.subheader('기술 통계')
  st.write(df.describe())
else:
  st.info('☝️ CSV 파일을 업로드하세요')
```

## 추가 정보
1. [`st.file_uploader`](https://docs.streamlit.io/library/api-reference/widgets/st.file_uploader)
2. [구성 옵션 설정하기](https://docs.streamlit.io/library/advanced-features/configuration#set-configuration-options)
