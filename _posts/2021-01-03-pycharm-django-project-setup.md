---
title: "[Django] Pycharm을 사용하여 Django 프레임워크 프로젝트 생성하기"
date: 2021-01-03 00:10:00 -0000
categories:
  - Django
  - Pycharm
---

## 1. 새로운 Django 프레임워크 프로젝트 생성

File - New Project - Django를 클릭합니다.

Location 항목에 프로젝트 이름을 입력합니다.

Project Interpreter: New Virtualenv environment를 클릭합니다.

New environment using 항목에서는

- Location: 프로젝트 별 패키지 환경을 분리하기 위해 파이썬이 제공하는 가상환경(Virtualenv)을 사용합니다. 아나콘다가 제공하는 Conda 가상 환경을 사용할 수도 있습니다.

- Base interpreter: 사용할 파이썬 언어 버전을 지정합니다.

More Settings를 클릭합니다.

- Template language: 템플릿 언어로 기본 Django 템플릿 언어를 사용할지 Jinja2를 사용할지 선택할 수 있습니다.

- Templates folder: 템플릿 파일들이 저장될 디렉토리 이름입니다. 기본값으로 templates가 지정되어 있습니다.

- Application name: 프로젝트 내 애플리케이션을 생성할 경우 이름을 입력합니다.
  
마지막으로 Create를 입력합니다.
  
이렇게 하면

```
django-admin startproject 프로젝트명
```

명령어를 통해 새로운 프로젝트를 생성하고

해당 프로젝트의 루트 디렉토리 경로에서

```
python manage.py startapp 애플리케이션명
```

명령어를 통해 새로운 애플리케이션을 생성한 것과 동일한 과정이 수행됩니다.

추가로 templates 폴더까지 생성됩니다.

프로젝트 설정 파일인 setting.py 파일을 보면

INSTALLED_APPS 값에 새로 생성한 애플리케이션의 설정 클래스가 등록되어 있음을 알 수 있습니다.

그 외 데이터베이스 엔진, 타임존, 정적 파일을 위한 설정 값이 지정되어 있습니다.

## 2. GitHub에 레포지토리 생성 및 프로젝트 연결

먼저 GitHub에서 레포지토리를 생성합니다.

Django 프로젝트의 루트 디렉토리 경로에 .gitignore 파일을 생성하여 가상 환경 설정 폴더, 기타 설정 파일 등을 추적하지 않도록 합니다.

[https://www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore) 사이트를 이용하면 운영체제, IDE, 프레임워크 별로 손쉽게 .gitignore 파일 내용을 구성할 수 있습니다.

이제 Pycharm에서 생성한 Django 프로젝트의 루트 경로에서 터미널을 실행하여 다음 git 명령어를 차례대로 입력합니다.

```
git init
```

```
git add -A
```

```
git commit -m "커밋 메시지 입력"
```

```
git branch -M main
```

```
git remote add origin GitHub_레포지토리_URL
```

```
git push -u origin main
```

## 3. Pycharm에서 GitHub 레포지토리 클론 및 프로젝트 구성
GitHub에 레포지토리를 생성한 상태에서 Pycharm에서 해당 레포지토리를 클론하여 새로운 Django 프레임워크 프로젝트를 생성할 수도 있습니다.

Git - Clone을 클릭합니다.

해당 레포지토리 URL을 입력한 후 Clone을 클릭합니다.

Pycharm에서 새로 프로젝트를 구성하지 않았으므로 가상 환경 설정이 필요합니다.

File - Setting을 클릭합니다.

Project: 프로젝트명 밑의 Python Interpreter를 클릭합니다.

Python Interpreter: <No interpreter> 오른쪽의 설정 아이콘을 클릭한 후 Add를 클릭합니다. Virtualenv interpreter를 클릭한 후 Location, Base interpreter를 지정한 다음 OK를 클릭합니다. 해당 경로에 venv 폴더가 생성되고 파이썬 패키지를 관리할 수 있게 되었습니다.

하단의 + 버튼을 클릭하고 "Django"를 입력하여 패키지를 검색합니다. "Django" 패키지를 선택하고 Install Package를 클릭합니다.

패키지가 성공적으로 설치되었다는 메시지를 확인한 후 OK 버튼을 클릭합니다.

이제 프로젝트 루트 폴더를 우클릭하여 Open In - Terminal을 클릭하면 해당 가상 환경에서 파이썬 인터프리터를 사용할 수 있습니다.


```
python manage.py runserver
```

명령어를 입력하여 Django 프레임워크의 정상 작동을 확인합니다.


