# st.form

`st.form`은 "제출" 버튼을 포함하여 요소들을 함께 묶는 양식을 생성합니다.

일반적으로 사용자가 위젯과 상호작용할 때마다 Streamlit 앱이 다시 실행됩니다.

양식은 다른 요소 및 위젯들을 시각적으로 그룹화하는 컨테이너이며, 제출 버튼을 포함합니다. 여기서 사용자는 제출 버튼을 누를 때까지 원하는 만큼 여러 위젯과 여러 번 상호작용할 수 있으며, 이는 앱의 재실행을 일으키지 않습니다. 마지막으로, 양식의 제출 버튼이 눌리면 양식 내의 모든 위젯 값들이 한 번에 Streamlit에 전송됩니다.

양식 객체에 요소를 추가하려면 `with` 표기법(선호됨)을 사용하거나, 변수에 할당한 후 Streamlit 메소드를 적용함으로써 양식에 메소드를 직접 호출하는 객체 표기법을 사용할 수 있습니다. 예제 앱에서 확인해 보세요.

양식에는 몇 가지 제약 사항이 있습니다:
- 모든 양식은 `st.form_submit_button`을 포함해야 합니다.
- `st.button`과 `st.download_button`은 양식에 추가할 수 없습니다.
- 양식은 앱의 어디에나(사이드바, 칼럼 등) 나타날 수 있지만, 다른 양식 내에 포함될 수는 없습니다.

양식에 대한 자세한 정보는 [블로그 게시물](https://blog.streamlit.io/introducing-submit-button-and-forms/)을 확인해보세요.

## 데모 앱

[![Streamlit 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/st.form/)

## 코드
`st.form`을 사용하는 방법은 다음과 같습니다:
```python
import streamlit as st

st.title('st.form')

# 'with' 표기법을 사용한 전체 예시
st.header('1. `with` 표기법 사용 예시')
st.subheader('커피 머신')

with st.form('my_form'):
    st.subheader('**커피 주문하기**')
    
    # 입력 위젯
    coffee_bean_val = st.selectbox('커피콩', ['아라비카', '로부스타'])
    coffee_roast_val = st.selectbox('커피 로스팅', ['라이트', '미디엄', '다크'])
    brewing_val = st.selectbox('추출 방법', ['에어로프레스', '드립', '프렌치 프레스', '모카 포트', '사이폰'])
    serving_type_val = st.selectbox('서빙 형식', ['핫', '아이스', '프라페'])
    milk_val = st.select_slider('우유 정도', ['없음', '낮음', '중간', '높음'])
    owncup_val = st.checkbox('자신의 컵 가져오기')
    
    # 모든 양식은 제출 버튼을 가져야 함
    submitted = st.form_submit_button('제출')

if submitted:
    st.markdown(f'''
        ☕ 주문하신 내용:
        - 커피콩: `{coffee_bean_val}`
        - 커피 로스팅: `{coffee_roast_val}`
        - 추출 방법: `{brewing_val}`
        - 서빙 형식: `{serving_type_val}`
        - 우유: `{milk_val}`
        - 자신의 컵 가져오기: `{owncup_val}`
        ''')
else:
    st.write('☝️ 주문하세요!')


# 객체 표기법을 사용한 짧은 예시
st.header('2. 객체 표기법 예시')

form = st.form('my_form_2')
selected_val = form.slider('값 선택')
form.form_submit_button('제출')

st.write('선택된 값: ', selected_val)
```

## 줄별 설명
Streamlit 앱을 만들 때 가장 먼저 할 일은 다음과 같이 `streamlit` 라이브러리를 `st`로 임포트하는 것입니다:
```python
import streamlit as st
```

이어서 앱에 대한 제목 텍스트를 생성합니다:
```python
st.title('st.form')
```

### 첫 번째 예시
첫 번째 예시로, `with` 표기법을 사용하여 `st.form` 명령을 적용합니다. 양식 안에서는 `커피 주문하기`라는 소제목을 시작으로, 여러 입력 위젯(`st.selectbox`, `st.select_slider`, `st.checkbox`)을 사용하여 커피 주문에 대한 정보를 수집합니다. 마지막으로, `st.form_submit_button` 명령을 통해 제출 버튼을 생성하며, 이 버튼을 클릭하면 모든 사용자 입력이 앱으로 한 번에 전송되어 처리됩니다.
```python
# 'with' 표기법을 사용한 전체 예시
st.header('1. `with` 표기법 사용 예시')
st.subheader('커피 머신')

with st.form('my_form'):
    st.subheader('**커피 주문하기**')

    # 입력 위젯
    coffee_bean_val = st.selectbox('커피콩', ['아라비카', '로부스타'])
    coffee_roast_val = st.selectbox('커피 로스팅', ['라이트', '미디엄', '다크'])
    brewing_val = st.selectbox('추출 방법', ['에어로프레스', '드립', '프렌치 프레스', '모카 포트', '사이폰'])
    serving_type_val = st.selectbox('서빙 형식', ['핫', '아이스', '프라페'])
    milk_val = st.select_slider('우유 정도', ['없음', '낮음', '중간', '높음'])
    owncup_val = st.checkbox('자신의 컵 가져오기')
    
    # 모든 양식은 제출 버튼을 가져야 함.
    submitted = st.form_submit_button('제출')
```

제출 버튼을 클릭한 후에 발생하는 로직을 추가합니다. 기본적으로 Streamlit 앱이 로드될 때마다 `else` 문이 실행되고, `☝️ 주문하세요!`라는 메시지가 표시됩니다. 반면 제출 버튼을 클릭하면, 여러 위젯을 통해 제공된 모든 사용자 입력이 여러 변수(예: `coffee_bean_val`, `coffee_roast_val` 등)에 저장되고 `st.markdown` 명령을 사용하여 f-string으로 출력됩니다.
```python
if submitted:
    st.markdown(f'''
        ☕ 주문하신 내용:
        - 커피콩: `{coffee_bean_val}`
        - 커피 로스팅: `{coffee_roast_val}`
        - 추출 방법: `{brewing_val}`
        - 서빙 형식: `{serving_type_val}`
        - 우유: `{milk_val}`
        - 자신의 컵 가져오기: `{owncup_val}`
        ''')
else:
    st.write('☝️ 주문하세요!')
```


### 두 번째 예시
이제 객체 표기법을 사용하여 `st.form`을 사용하는 두 번째 예시로 넘어갑니다. 여기서 `st.form` 명령은 `form` 변수에 할당됩니다. 이후에 `slider`나 `form_submit_button`과 같은 여러 Streamlit 명령들이 `form` 변수에 적용됩니다.
```python
# 객체 표기법을 사용한 짧은 예시
st.header('2. 객체 표기법 예시')

form = st.form('my_form_2')
selected_val = form.slider('값 선택')
form.form_submit_button('제출')

st.write('선택된 값: ', selected_val)
```

## 추가 읽기
- [`st.form`](https://docs.streamlit.io/library/api-reference/control-flow/st.form)
- [제출 버튼 및 양식 소개](https://blog.streamlit.io/introducing-submit-button-and-forms/)
