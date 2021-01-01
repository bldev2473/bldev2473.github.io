---
title: "[Django, Vue.js] Django 및 Vue.js 프레임워크에서 웹팩(Webpack) 사용하기 1"
date: 2021-01-01 00:10:00 -0000
categories: Django, Vue.js, Webpack
---

웹팩(Webpack)은 모듈 번들러(module bundler)입니다.

웹 페이지를 구성하는 자원들 중 정적(static) 자원들을 손쉽게 관리하는 것이 웹팩의 주 사용 목적입니다.

[https://webpack.js.org/concepts/](https://webpack.js.org/concepts/)의 개념 설명은 다음과 같습니다.

>
> At its core, webpack is a static module bundler for modern JavaScript applications. When webpack processes your application, it internally builds a dependency graph which maps every module your project needs and generates one or more bundles.

웹팩은 자바스크립트 애플리케이션을 위한 정적 모듈 번들러이며, 모듈 간 의존성을 내부적으로 구성 및 관리하여 하나(또는 그 이상)의 번들로 만들어준다는 것이 핵심 개념입니다.

## Vue CLI와 웹팩
[https://github.com/vuejs/vue-cli/blob/dev/docs/guide/webpack.md](https://github.com/vuejs/vue-cli/blob/dev/docs/guide/webpack.md)
