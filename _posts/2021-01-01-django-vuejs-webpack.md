---
title: "[Django, Vue.js] Django 및 Vue.js 프레임워크에서 웹팩(Webpack) 사용하기 1"
date: 2021-01-01 00:10:00 -0000
categories: [Django, Vue.js, Webpack]
---

Webpack은 모듈 번들러(module bundler)입니다.

웹 페이지를 구성하는 자원들 중 정적(static) 자원들을 손쉽게 관리하는 것이 웹팩의 주 사용 목적입니다.

[https://webpack.js.org/concepts/](https://webpack.js.org/concepts/)에서의 웹팩에 대한 개념 설명은 다음과 같습니다.

>
>At its core, webpack is a static module bundler for modern JavaScript applications. When webpack processes your application, it internally builds a dependency graph which maps every module your project needs and generates one or more bundles.

Webpack은 자바스크립트 애플리케이션을 위한 정적 모듈 번들러이며, 프로젝트가 필요로 하는 모든 모듈 간 의존성을 내부적으로 의존성 그래프로 구성 및 관리하여 하나(또는 그 이상)의 번들로 만들어줍니다.

쉽게 말해 Webpack은 복잡하게 얽힌 정적 자원들을 단순히 하나의 자바스크립트 파일로 변환해줍니다.

Django 프레임워크는 내부적으로 정적 자원들을 처리하도록 되어있고([https://docs.djangoproject.com/en/3.0/howto/static-files/](https://docs.djangoproject.com/en/3.0/howto/static-files/)) 개발이 아닌 프로덕션을 위한 정적 파일 제공 방법도 존재합니다([https://docs.djangoproject.com/en/3.0/howto/static-files/deployment/](https://docs.djangoproject.com/en/3.0/howto/static-files/deployment/)). 따라서 Webpack이 프로젝트의 모든 정적 파일들을 하나의 자바스크립트 파일로 변환해주고, Django 프레임워크는 이 자바스크립트을 불러와 웹 페이지를 구성하도록 하면 됩니다.

먼저 다음과 같이 Django 프레임워크의 프로젝트를 구성합니다.

Django 프레임워크는 django.contrib.staticfiles라는 앱을 통해 정적 파일들을 제공하고 있으므로 프로젝트 구성 시 프로젝트의 setting.py 파일에 다음과 같은 설정이 필요합니다.

1. INSTALLED_APPS 값에 'django.contrib.staticfiles'를 포함시킵니다. => staticfiles라는 앱이 아래 설정들을 통해 프로젝트가 정적 파일들을 사용하여 웹 페이지를 구성할 수 있도록 만들어 줍니다. 
2. STATIC_ROOT를 지정합니다. => 정적 파일들이 위치한 절대 경로가 됩니다. Django의 collectstatic이라는 명령어는 staticfiles라는 앱이 이 절대 경로에 정적 파일들을 모아두게 합니다. Apache나 Nginx와 같은 별도의 웹 서버에 이 디렉토리만 알려주면 됩니다.

## Vue CLI와 웹팩
[https://github.com/vuejs/vue-cli/blob/dev/docs/guide/webpack.md](https://github.com/vuejs/vue-cli/blob/dev/docs/guide/webpack.md)
