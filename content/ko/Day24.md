# st.cache

`st.cache`는 Streamlit 앱의 성능을 최적화하는 데 도움을 줍니다.

Streamlit은 웹에서 데이터를 로드하거나, 큰 데이터셋을 조작하거나, 비용이 많이 드는 계산을 수행할 때 앱의 성능을 유지할 수 있게 하는 캐싱 메커니즘을 제공합니다. 이는 `@st.cache` 데코레이터를 사용하여 수행됩니다.

함수에 @st.cache 데코레이터를 표시하면 Streamlit에 다음과 같은 몇 가지 사항을 확인하도록 지시합니다:

1. 함수를 호출할 때 사용한 입력 매개변수
2. 함수에서 사용된 모든 외부 변수의 값
3. 함수의 본문
4. 캐시된 함수 내에서 사용된 모든 함수의 본문

이 네 가지 구성 요소가 이러한 정확한 값과 순서로 Streamlit에 처음 나타난 경우, Streamlit은 함수를 실행하고 결과를 로컬 캐시에 저장합니다. 그 후에 캐시된 함수가 호출될 때 이러한 구성 요소 중 어느 것도 변경되지 않으면 Streamlit은 함수를 실행하지 않고 대신 캐시에 저장된 이전 출력을 반환합니다.

Streamlit이 이러한 구성 요소의 변경 사항을 추적하는 방법은 해싱을 통한 것입니다. 캐시를 메모리 내 키-값 저장소로 생각해보세요. 여기서 키는 위의 모든 것의 해시이고, 값은 참조에 의해 전달된 실제 출력 객체입니다.

마지막으로, `@st.cache`는 캐시의 동작을 구성하는 데 사용할 수 있는 인수를 지원합니다. 이에 대한 자세한 정보는 API 참조에서 찾을 수 있습니다.

## 사용 방법?

Streamlit 앱에서 정의하는 사용자 정의 함수의 앞줄에 `st.cache` 데코레이터를 추가하기만 하면 됩니다. 아래 예제를 참고하세요.

## 데모 앱

[![Streamlit 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.cache/)

## 코드
`st.cache`를 사용하는 방법은 다음과 같습니다:
```python
import streamlit as st
import numpy as np
import pandas as pd
from time import time

st.title('st.cache')

# 캐시 사용
a0 = time()
st.subheader('st.cache 사용')

@st.cache(suppress_st_warning=True)
def load_data_a():
  df = pd.DataFrame(
    np.random.rand(2000000, 5),
    columns=['a', 'b', 'c', 'd', 'e']
  )
  return df

st.write(load_data_a())
a1 = time()
st.info(a1-a0)


# 캐시 미사용
b0 = time()
st.subheader('st.cache 미사용')

def load_data_b():
  df = pd.DataFrame(
    np.random.rand(2000000, 5),
    columns=['a', 'b', 'c', 'd', 'e']
  )
  return df

st.write(load_data_b())
b1 = time()
st.info(b1-b0)
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로, 그리고 앱에서 사용되는 다른 라이브러리를 임포트하는 것입니다:
```python
import streamlit as st
import numpy as np
import pandas as pd
from time import time
```

이어서 앱에 대한 제목 텍스트를 생성합니다:
```python
st.title('st.cache')
```

다음으로, 큰 DataFrame을 생성하는 두 개의 사용자 정의 함수를 정의합니다. 첫 번째 함수는 `st.cache` 데코레이터를 사용하고

, 두 번째 함수는 사용하지 않습니다:
```python
@st.cache(suppress_st_warning=True)
def load_data_a():
  df = pd.DataFrame(
    np.random.rand(2000000, 5),
    columns=['a', 'b', 'c', 'd', 'e']
  )
  return df

def load_data_b():
  df = pd.DataFrame(
    np.random.rand(2000000, 5),
    columns=['a', 'b', 'c', 'd', 'e']
  )
  return df
```

마지막으로, `time()` 명령을 사용하여 실행 시간을 측정하면서 사용자 정의 함수를 실행합니다.
```python
# 캐시 사용
a0 = time()
st.subheader('st.cache 사용')

# 여기에 load_data_a 함수 삽입

st.write(load_data_a())
a1 = time()
st.info(a1-a0)

# 캐시 미사용
b0 = time()
st.subheader('st.cache 미사용')

# 여기에 load_data_b 함수 삽입

st.write(load_data_b())
b1 = time()
st.info(b1-b0)
```

첫 실행 시 두 함수의 실행 시간이 비슷할 수 있습니다. 앱을 다시 로드하고 `st.cache` 데코레이터를 사용할 때 실행 시간이 어떻게 변하는지 주목해보세요. 속도가 빨라진 것을 관찰할 수 있나요?

## 추가 읽기
- [`st.cache` API 문서](https://docs.streamlit.io/library/api-reference/performance/st.cache)
- [`st.cache`를 사용한 성능 최적화](https://docs.streamlit.io/library/advanced-features/caching)
- [실험적 캐시 프리미티브](https://docs.streamlit.io/library/advanced-features/experimental-cache-primitives)
- [`st.experimental_memo`](https://docs.streamlit.io/library/api-reference/performance/st.experimental_memo)
- [`st.experimental_singleton`](https://docs.streamlit.io/library/api-reference/performance/st.experimental_singleton)
