# 스트림릿 앱 만들기의 예술

오늘은 *#30DaysOfStreamlit* 챌린지의 30일째입니다. 이 챌린지까지 오신 것을 축하드립니다.

이 튜토리얼에서는 이러한 학습 챌린지에서 얻은 새로운 지식을 활용하여 실제 문제를 해결하기 위한 스트림릿 앱을 만들어 볼 것입니다.

## 실제 문제

콘텐츠 제작자로서 YouTube 동영상의 썸네일 이미지에 액세스하는 것은 소셜 프로모션 및 콘텐츠 제작을 위한 유용한 자원입니다.

이 문제를 해결하고 스트림릿 앱을 만드는 방법을 알아봅시다.

## 해결책

오늘 우리는 YouTube 동영상에서 썸네일 이미지를 추출할 수 있는 스트림릿 앱인 `yt-img-app`을 만들 것입니다.

간단히 말해, 스트림릿 앱이 수행해야 할 3단계는 다음과 같습니다:

1. 사용자로부터 YouTube URL을 입력으로 받기
2. URL의 텍스트 처리를 수행하여 고유한 YouTube 비디오 ID 추출하기
3. YouTube 비디오의 썸네일 이미지를 검색하고 표시하는 사용자 정의 함수에 YouTube 비디오 ID를 입력으로 사용하기

## 사용 방법

스트림릿 앱을 사용하기 위해서는 YouTube URL을 입력 텍스트 상자에 복사하여 붙여넣으세요.

## 데모 앱

[![스트림릿 앱](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/dataprofessor/yt-img-app/)

## 코드
`yt-img-app` 스트림릿 앱을 만드는 방법은 다음과 같습니다:
```python
import streamlit as st

st.title('🖼️ yt-img-app')
st.header('YouTube 썸네일 이미지 추출기 앱')

with st.expander('이 앱에 대하여'):
  st.write('이 앱은 YouTube 동영상의 썸네일 이미지를 검색합니다.')
  
# 이미지 설정
st.sidebar.header('설정')
img_dict = {'Max': 'maxresdefault', 'High': 'hqdefault', 'Medium': 'mqdefault', 'Standard': 'sddefault'}
selected_img_quality = st.sidebar.selectbox('이미지 품질 선택', ['Max', 'High', 'Medium', 'Standard'])
img_quality = img_dict[selected_img_quality]

yt_url = st.text_input('YouTube URL 붙여넣기', 'https://youtu.be/JwSS70SZdyM')

def get_ytid(input_url):
  if 'youtu.be' in input_url:
    ytid = input_url.split('/')[-1]
  if 'youtube.com' in input_url:
    ytid = input_url.split('=')[-1]
  return ytid
    
# YouTube 썸네일 이미지 표시
if yt_url != '':
  ytid = get_ytid(yt_url) # yt or yt_url

  yt_img = f'http://img.youtube.com/vi/{ytid}/{img_quality}.jpg'
  st.image(yt_img)
  st.write('YouTube 동영상 썸네일 이미지 URL: ', yt_img)
else:
  st.write('☝️ URL을 입력해 계속하세요 ...')
```

## 줄별 설명
스트림릿 앱을 만들 때 가장 먼저 할 일은 `streamlit` 라이브러리를 `st`로 가져오는 것입니다:
```python
import streamlit as st
```

다음으로, 앱의 제목과 헤더를 표시합니다:
```python
st.title('🖼️ yt-img-app')
st.header('YouTube 썸네일 이미지 추출기 앱')
```
이와 동시에, 우리는 "이 앱에 대하여" 확장 가능한 상자를 추가할 수도 있습니다.
```python
with st.expander('이 앱에 대하여'):
  st.write('이 앱은 YouTube 동영상의 썸네일 이미지를 검색합니다.')
 
여기에서, 사용자 입력에 따라 사용할 이미지 품질을 선택하기 위한 선택 상자를 만듭니다.
```python
# 이미지 설정
st.sidebar.header('설정')
img_dict = {'Max': 'maxresdefault', 'High': 'hqdefault', 'Medium': 'mqdefault', 'Standard': 'sddefault'}
selected_img_quality = st.sidebar.selectbox('이미지 품질 선택', ['Max', 'High', 'Medium', 'Standard'])
img_quality = img_dict[selected_img_quality]
```

이미지를 추출할 YouTube 동영상 URL을 입력할 수 있는 입력 텍스트 상자를 표시합니다.
```python
yt_url = st.text_input('YouTube URL 붙여넣기', 'https://youtu.be/JwSS70SZdyM')
```

입력 URL의 텍스트 처리를 수행하는 사용자 정의 함수입니다.
```python
def get_ytid(input_url):
  if 'youtu.be' in input_url:
    ytid = input_url.split('/')[-1]
  if 'youtube.com' in input_url:
    ytid = input_url.split('=')[-1]
  return ytid
```

마지막으로, URL을 입력하라는 알림을 표시할지 (즉, `else` 문에서와 같이) 또는 YouTube 썸네일 이미지를 표시할지 (즉, `if` 문에서와 같이) 결정하기 위해 흐름 제어를 사용합니다.
```python
# YouTube 썸네일 이미지 표시
if yt_url != '':
  ytid = get_ytid(yt_url) # yt or yt_url

  yt_img = f'http://img.youtube.com/vi/{ytid}/{img_quality}.jpg'
  st.image(yt_img)
  st.write('YouTube 동영상 썸네일 이미지 URL: ', yt_img)
else:
  st.write('☝️ URL을 입력해 계속하세요 ...')
```

## 요약

요약하자면, 어떤 스트림릿 앱을 만들 때, 우리는 보통 먼저 문제를 식별하고 정의하는 것으로 시작합니다. 다음으로, 우리는 그 문제를 해결하기 위해 그것을 세부적인 단계로 나누고 스트림릿 앱에서 이를 구현합니다.

여기에서 우리는 또한 사용자로부터 필요한 데이터나 정보를 결정하고, 최종적으로 원하는 결과물을 생산하기 위해 사용자 입력을 처리하는 접근 방법과 방식을 결정해야 합니다.

이 튜토리얼을 즐기셨기를 바랍니다, 스트림릿을 즐기세요!
