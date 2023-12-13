# 로컬 개발 환경 설정하기

Streamlit 앱 구축을 시작하기 전에, 먼저 개발 환경을 설정해야 합니다.

conda 환경을 설치하고 설정하는 것부터 시작해 봅시다.

## **conda 설치하기**
- <https://docs.conda.io/en/latest/miniconda.html>로 이동하여 운영 체제(Windows, Mac 또는 Linux)를 선택하고 `conda`를 설치합니다.
- 설치 프로그램을 다운로드하여 실행하여 `conda`를 설치합니다.

## **새로운 conda 환경 만들기**
이제 conda가 설치되었으니, Python 라이브러리 종속성을 관리하기 위한 conda 환경을 만들어 봅시다.

Python 3.9로 새 환경을 만들려면 다음을 입력하세요:
```bash
conda create -n stenv python=3.9
```

여기서 `create -n stenv`는 `stenv`라는 이름의 conda 환경을 생성하고, `python=3.9`는 Python 버전 3.9로 conda 환경을 설정합니다.

## **conda 환경 활성화하기**

`stenv`라고 이름 지어진 우리가 방금 만든 conda 환경을 사용하기 위해 커맨드 라인에 다음을 입력하세요:

```bash
conda activate stenv
```

## **Streamlit 라이브러리 설치하기**

이제 `streamlit` 라이브러리를 설치할 시간입니다:
```bash
pip install streamlit
```

## **Streamlit 데모 앱 실행하기**
Streamlit 데모 앱(그림 1)을 실행하려면 다음을 입력하세요:
```bash
streamlit hello
```