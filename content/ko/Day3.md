# st.button 사용하기

`st.button`은 버튼 위젯을 표시하는 데 사용됩니다.

## 우리가 만들 것은?

버튼이 눌렸는지 여부에 따라 조건적으로 다른 메시지를 출력하는 간단한 앱입니다.

앱의 흐름:

1. 기본적으로 앱은 `Goodbye`를 출력합니다.
2. 버튼을 클릭하면 앱은 대체 메시지 `Why hello there`를 표시합니다.

## 데모 앱

배포된 Streamlit 앱은 아래 링크에 표시된 것처럼 보일 것입니다:

[![Streamlit 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.button/)

## 코드

위에 언급된 앱을 구현하기 위한 코드는 다음과 같습니다:

```python
import streamlit as st

st.header('st.button')

if st.button('Say hello'):
     st.write('Why hello there')
else:
     st.write('Goodbye')
```

## 코드 설명

Streamlit 앱을 만들 때 가장 먼저 해야 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 임포트하는 것입니다:

```python
import streamlit as st
```

그 다음에는 앱의 헤더 텍스트를 생성합니다:

```python
st.header('st.button')
```

그 다음, `if`와 `else` 조건문을 사용하여 대체 메시지를 출력합니다.

```python
if st.button('Say hello'):
     st.write('Why hello there')
else:
     st.write('Goodbye')
```

위 코드 상자에서 볼 수 있듯이, `st.button()` 명령은 `Say hello`라는 `label` 입력 인수를 받아들입니다. 이는 버튼에 표시되는 텍스트입니다.

버튼이 클릭되었는지 여부에 따라 `Why hello there` 또는 `Goodbye`라는 텍스트 메시지를 출력하기 위해 `st.write` 명령을 사용합니다:

```python
st.write('Why hello there')
```

그리고

```python
st.write('Goodbye')
```

위 `st.write` 문장은 메시지를 대체적으로 표시하는 과정을 수행하기 위해 `if` 및 `else` 조건문 아래에 배치되는 것이 중요합니다.

## 다음 단계

이제 로컬에서 Streamlit 앱을 만들었으니, 곧 다가올 챌린지에서 설명될 [Streamlit 커뮤니티 클라우드](https://streamlit.io/cloud)에 배포할 차례입니다.

이번 주가 여러분의 챌린지 첫 주이므로, 위 코드 상자에 표시된 전체 코드와 이 웹페이지 내부의 솔루션(데모 앱)을 제공합니다.

다음 챌린지에서는 먼저 스스로 Streamlit 앱을 구현해 보는 것이 권장됩니다.

걱정하지 마세요, 만약 막히면 솔루션을 살펴볼 수 있습니다.

## 참고 자료

Streamlit API 문서에서 [`st.button`](https://docs.streamlit.io/library/api-reference/widgets/st.button)에 대해 읽어보세요.
