# Streamlit 컴포넌트

컴포넌트는 Streamlit의 가능성을 확장하는 타사 Python 모듈입니다[[1](https://docs.streamlit.io/library/components)].

## 사용 가능한 Streamlit 컴포넌트는 무엇인가요?

Streamlit 웹사이트에는 여러 가지 Streamlit 컴포넌트들이 소개되어 있습니다[[2](https://streamlit.io/components)].

Fanilo(한 Streamlit 크리에이터)는 위키 게시글에서 약 85개의 Streamlit 컴포넌트를 정리한 놀라운 목록을 만들었습니다(2022년 4월 기준)[[3](https://discuss.streamlit.io/t/streamlit-components-community-tracker/4634)].

## 사용 방법은?

Streamlit 컴포넌트는 pip을 통해 간단히 설치할 수 있습니다.

이 튜토리얼에서는 `streamlit_pandas_profiling` 컴포넌트[[4](https://share.streamlit.io/okld/streamlit-gallery/main?p=pandas-profiling)] 사용을 시작하는 방법을 안내해드리겠습니다.

#### 컴포넌트 설치 

```bash
pip install streamlit_pandas_profiling
```

## 데모 앱

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/streamlit-components/)

## 코드
컴포넌트를 사용하여 Streamlit 앱을 구축하는 방법은 다음과 같습니다:
```python
import streamlit as st
import pandas as pd
import pandas_profiling
from streamlit_pandas_profiling import st_profile_report

st.header('`streamlit_pandas_profiling`')

df = pd.read_csv('https://raw.githubusercontent.com/dataprofessor/data/master/penguins_cleaned.csv')

pr = df.profile_report()
st_profile_report(pr)
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
import pandas as pd
import pandas_profiling
from streamlit_pandas_profiling import st_profile_report
```

이는 앱에 대한 헤더 텍스트를 만드는 것으로 이어집니다:
```python
st.header('`streamlit_pandas_profiling`')
```

다음으로, 펭귄 데이터셋을 `pandas`의 `read_csv` 명령어를 사용하여 불러옵니다.
```python
df = pd.read_csv('https://raw.githubusercontent.com/dataprofessor/data/master/penguins_cleaned.csv')
```

마지막으로, `profile_report()` 명령어를 통해 생성된 판다스 프로파일링 보고서를 `st_profile_report`를 사용하여 표시합니다:
```python
pr = df.profile_report()
st_profile_report(pr)
```

## 자체 컴포넌트 만들기

자체 컴포넌트를 만들고 싶다면, 다음 자료를 확인하세요:
- [컴포넌트 만들기](https://docs.streamlit.io/library/components/create)
- [컴포넌트 게시하기](https://docs.streamlit.io/library/components/publish)
- [컴포넌트 API](https://docs.streamlit.io/library/components/components-api)
- [컴포넌트에 관한 블로그 글](https://blog.streamlit.io/introducing-streamlit-components/)

비디오를 통해 배우는 것을 선호한다면, 엔지니어 Tim Conkling이 만든 훌륭한 튜토리얼을 확인해 보세요:
- [Streamlit 컴포넌트 만들기 | 1부: 설정 및 아키텍처](https://youtu.be/BuD3gILJW-Q)
- [Streamlit 컴포넌트 만들기 | 2부: 슬라이더 위젯 만들기](https://youtu.be/QjccJl_7Jco)

## 컴포넌트에 관한 추가 정보
1. [Streamlit 컴포넌트 - API 문서](https://docs.streamlit.io/library/components)
2. [주요 Streamlit 컴포넌트](https://streamlit.io/components)
3. [Streamlit 컴포넌트 - 커뮤니티 추적기](https://discuss.streamlit.io/t/streamlit-components-community-tracker/4634)
4. [`streamlit_pandas_profiling`](https://share.streamlit.io/okld/streamlit-gallery/main?p=pandas-profiling)
