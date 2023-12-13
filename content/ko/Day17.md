# st.secrets

`st.secrets`를 사용하면 API 키, 데이터베이스 비밀번호 또는 기타 자격 증명과 같은 기밀 정보를 저장할 수 있습니다.

## 데모 앱

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.secrets/)

## 코드
`st.secrets` 사용 방법은 다음과 같습니다:
```python
import streamlit as st

st.title('st.secrets')

st.write(st.secrets['message'])
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
```

이는 앱에 대한 제목 텍스트를 만드는 것으로 이어집니다:
```python
st.title('st.secrets')
```

마지막으로, 저장된 기밀 정보를 표시합니다:
```python
st.write(st.secrets['message'])
```

Streamlit Community Cloud에서 아래 스크린샷과 같이 기밀 정보를 저장할 수 있다는 점을 유의해야 합니다.

로컬에서 작업하는 경우, `.streamlit/secrets.toml`에 저장할 수 있지만, 앱을 배포할 때 GitHub 리포지토리에 업로드하지 않도록 주의해야 합니다.

## 추가 정보
- [Streamlit 앱에 기밀 정보 추가하기](https://blog.streamlit.io/secrets-in-sharing-apps/)
- [기밀 정보 관리](https://docs.streamlit.io/streamlit-cloud/get-started/deploy-an-app/connect-to-data-sources/secrets-management)
