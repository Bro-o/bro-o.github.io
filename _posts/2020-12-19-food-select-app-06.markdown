---
title: "Food Select App - 06 호스팅"
layout: post
date: 2020-12-19 22:10
tag: web
headerImage: true
projects: true
hidden: true # don't count this post in blog pagination
description: "This is a simple and minimalist template for Jekyll."
category: project
author: Yun
externalLink: false
---


 0. 프로젝트 구상
 1. 랜덤 이미지
 2. 체크박스 카테고리
 3. 디자인 적용
 4. 사이드 메뉴
 5. 장바구니
 6. 호스팅

# 6. 호스팅
Firebase를 이용하여 서버를 구축하여 호스팅 및 배포를 하였다. Firebase를 추가하는 방법은 홈페이지에 상세하게 나와있다. 
npm(노드 패키지 관리자)을 사용하여 Firebase CLI를 설치하려면 다음 단계를 따르세요.
[Node.js](https://www.nodejs.org/)를 설치한다. Node.js를 설치하면 npm 명령어 도구가 자동으로 설치된다.
다음 명령어를 실행하여 npm으로 Firebase CLI를 설치한다.
```
$ npm install -g firebase-tools
```
CLI를 설치한 후에는 인증해야 한다. 그러면 Firebase 프로젝트를 나열하여 인증을 확인할 수 있다.
다음 명령어를 실행하여 Google 계정으로 Firebase에 로그인한다.
```
$ firebase login
```
Firebase 프로젝트를 초기화합니다.
```
$ firebase init
```
![checkbox](https://bro-o.github.io/assets/images/firebase1.png)
**“Hosting”**을 선택해준다.
![checkbox](https://bro-o.github.io/assets/images/firebase2.png)
이 전에 firebase에서 프로젝트를 생성했다면 **“Use an existing project”**, 아니라면 **“Create a new projct”**를 선택한다.

초기 설정이 마무리 된 후 배포해주면 된다.
```
$ firebase deploy --only hosting
```
[swing 2 app](http://www.swing2app.co.kr/)에 적용하여 apk 파일을 뽑아내면 어플로 만들 수 있다.

## 추가
Firebase 시작하기 : https://firebase.google.com/docs/web/setup?authuser=0
Food Select App url : [food-e0bbf.firebaseapp.com](https://food-e0bbf.firebaseapp.com/)

