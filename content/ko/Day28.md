# streamlit-shap

[`streamlit-shap`](https://github.com/snehankekre/streamlit-shap)는 [SHAP](https://github.com/slundberg/shap) 플롯을 [Streamlit](https://streamlit.io/)에서 표시하기 위한 래퍼를 제공하는 Streamlit 컴포넌트입니다.

이 라이브러리는 저희 내부 직원인 [스네한 케크레](https://github.com/snehankekre)(Snehan Kekre)가 개발했으며, [Streamlit 문서화](https://docs.streamlit.io/) 웹사이트도 관리합니다.

먼저, Streamlit을 설치한 후(당연하죠!) `streamlit-shap` 라이브러리를 pip로 설치합니다:
```bash
pip install streamlit
pip install streamlit-shap
```

또한, 아직 설치하지 않았다면 다른 필수 라이브러리들(예: `matplotlib`, `pandas`, `scikit-learn`, `xgboost`)도 설치해야 합니다.


## 데모 앱

[![Streamlit 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/streamlit-shap/)

## 코드
`streamlit-shap`를 사용하는 방법은 다음과 같습니다:
```python
import streamlit as st
from streamlit_shap import st_shap
import shap
from sklearn.model_selection import train_test_split
import xgboost
import numpy as np
import pandas as pd

st.set_page_config(layout="wide")

@st.experimental_memo
def load_data():
    return shap.datasets.adult()

@st.experimental_memo
def load_model(X, y):
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=7)
    d_train = xgboost.DMatrix(X_train, label=y_train)
    d_test = xgboost.DMatrix(X_test, label=y_test)
    params = {
        "eta": 0.01,
        "objective": "binary:logistic",
        "subsample": 0.5,
        "base_score": np.mean(y_train),
        "eval_metric": "logloss",
        "n_jobs": -1,
    }
    model = xgboost.train(params, d_train, 10, evals = [(d_test, "test")], verbose_eval=100, early_stopping_rounds=20)
    return model

st.title("`streamlit-shap`로 Streamlit 앱에서 SHAP 플롯 표시하기")

with st.expander('앱에 대하여'):
    st.markdown('''[`streamlit-shap`](https://github.com/snehankekre/streamlit-shap)는 [SHAP](https://github.com/slundberg/shap) 플롯을 [Streamlit](https://streamlit.io/)에서 표시하기 위한 래퍼를 제공하는 Streamlit 컴포넌트입니다.
                    이 라이브러리는 저희 내부 직원인 [스네한 케크레](https://github.com/snehankekre)가 개발했으며, [Streamlit 문서화](https://docs.streamlit.io/) 웹사이트도 관리합니다.
                ''')

st.header('입력 데이터')
X, y = load_data()
X_display, y_display = shap.datasets.adult(display=True)

with st.expander('데이터에 대하여'):
    st.write('예시 데이터셋으로 성인 인구 조사 데이터를 사용합니다.')
with st.expander('X'):
    st.dataframe(X)
with st.expander('y'):
    st.dataframe(y)

st.header('SHAP 출력')
 
# XGBoost 모델 훈련
model = load_model(X, y)

# SHAP 값 계산
explainer = shap.Explainer(model, X)
shap_values = explainer(X)

with st.expander('워터폴 플롯'):
    st_shap(shap.plots.waterfall(shap_values[0]), height=300)
with st.expander('비스웜 플롯'):
    st_shap(shap.plots.beeswarm(shap_values), height=300)

explainer = shap.TreeExplainer(model)
shap_values = explainer.shap_values(X)

with st.expander('포스 플롯'):
    st.subheader('첫 번째 데이터 인스턴스')
    st_shap(shap.force_plot(explainer.expected_value, shap_values[0,:], X_display.iloc[0,:]), height=200, width=1000)
    st.subheader('첫 천 번째 데이터 인스턴스')
    st_shap(shap.force_plot(explainer.expected_value, shap_values[:1000,:], X_display.iloc[:1000,:]), height=400, width=1000)
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
from streamlit_shap import st_shap
import shap
from sklearn.model_selection import train_test_split
import xgboost
import numpy as np
import pandas as pd
```

다음으로, Streamlit 앱의 내용이 전체 페이지 너비로 펼쳐질 수 있도록 페이지 레이아웃을 넓게 설정합니다.
```python
st.set_page_config(layout="wide")
```

그 다음으로, `shap` 라이브러리에서 데이터셋을 로드합니다:
```python
@st.experimental_memo
def load_data():
    return shap.datasets.adult()
```

그 다음으로, `X, y` 행렬 쌍을 입력으로 받아 데이터를 훈련/테스트 세트로 분할하고, `DMatrix`를 구성하며 XGBoost 모델을 빌드하는 `load_model`이라는 함수를 정의합니다.
```python
@st.experimental_memo
def load_model(X, y):
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=7)
    d_train = xgboost.DMatrix(X_train, label=y_train)
    d_test = xgboost.DMatrix(X_test, label=y_test)
    params = {
        "eta": 0.01,
        "objective": "binary:logistic",
        "subsample": 0.5,
        "base_score": np.mean(y_train),
        "eval_metric": "logloss",
        "n_jobs": -1,
    }
    model = xgboost.train(params, d_train, 10, evals = [(d_test, "test")], verbose_eval=100, early_stopping_rounds=20)
    return model
```

그 후 Streamlit 앱의 제목을 표시합니다:
```python
st.title("`streamlit-shap`로 Streamlit 앱에서 SHAP 플롯 표시하기")
```

앱에 대한 설명을 제공하기 위해 접을 수 있는 정보 박스를 구현합니다:
```python
with st.expander('앱에 대하여'):
    st.markdown('''[`streamlit-shap`](https://github.com/snehankekre/streamlit-shap)는 [SHAP](https://github.com/slundberg/shap) 플롯을 [Streamlit](https://streamlit.io/)에서 표시하기 위한 래퍼를 제공하는 Streamlit 컴포넌트입니다.
                    이 라이브러리는 저희 내부 직원인 [스네한 케크레](https://github.com/snehankekre)가 개발했으며, [Streamlit 문서화](https://docs.streamlit.io/) 웹사이트도 관리합니다.
                ''')
```

여기서 입력 데이터의 `X`와 `y` 변수에 대한 헤더 텍스트와 정보 박스를 표시합니다:
```python
st.header('입력 데이터')
X, y = load_data()
X_display, y_display = shap.datasets.adult(display=True)

with st.expander('데이터에 대하여'):
    st.write('예시 데이터셋으로 성인 인구 조사 데이터를 사용합니다.')
with st.expander('X'):
    st.dataframe(X)
with st.expander('y'):
    st.dataframe(y)
```

"여기서 우리는 다가오는 SHAP 출력에 대한 헤더 텍스트를 표시할 것입니다:"
```python
st.header('SHAP 출력')
```

그 후 `load_model` 함수를 사용하여 XGBoost 모델을 구축합니다. 마지막으로,
```python
# XGBoost 모델 훈련
X, y = load_data()
X_display, y_display = shap.datasets.adult(display=True)

model = load_model(X, y)
```

여기서 SHAP 값들을 계산합니다. 이 값들은 워터폴과 비스웜 플롯을 만드는 데 사용됩니다.
```python
# SHAP 값 계산
explainer = shap.Explainer(model, X)
shap_values = explainer(X)

with st.expander('워터폴 플롯'):
    st_shap(shap.plots.waterfall(shap_values[0]), height=300)
with st.expander('비스웜 플롯'):
    st_shap(shap.plots.beeswarm(shap_values), height=300)
```

마지막으로, 앙상블 트리 모델의 출력을 설명하기 위해 `shap.TreeExplainer` 명령을 사용하고 `shap.force_plot` 명령을 통해 시각화합니다:
```python
explainer = shap.TreeExplainer(model)
shap_values = explainer.shap_values(X)

with st.expander('포스 플롯'):
    st.subheader('첫 번째 데이터 인스턴스')
    st_shap(shap.force_plot(explainer.expected_value, shap_values[0,:], X_display.iloc[0,:]), height=200, width=1000)
    st.subheader('첫 천 번째 데이터 인스턴스')
    st_shap(shap.force_plot(explainer.expected_value, shap_values[:1000,:], X_display.iloc[:1000,:]), height=400, width=1000)
```

## 추가 정보
- [`streamlit-shap`](https://github.com/snehankekre/streamlit-shap)
- [SHAP](https://github.com/slundberg/shap)
