---
title: "Food Select App - 01 랜덤 이미지"
layout: post
date: 2020-09-05 22:10
tag: web
headerImage: true
projects: true
hidden: true # don't count this post in blog pagination
description: "This is a simple and minimalist template for Jekyll."
category: project
author: Yun
externalLink: false
---


 0. [프로젝트 구상](https://bro-o.github.io/food-select-app-00/)
 1. [랜덤 이미지](https://bro-o.github.io/food-select-app-01/)
 2. [체크박스 카테고리](https://bro-o.github.io/food-select-app-02/)
 3. [디자인 적용](https://bro-o.github.io/food-select-app-03/)
 4. [사이드 메뉴](https://bro-o.github.io/food-select-app-04/)
 5. [장바구니](https://bro-o.github.io/food-select-app-05/)
 6. [호스팅](https://bro-o.github.io/food-select-app-06/)
---
# 1. 랜덤이미지
제일 기본이 되는 기능인 버튼을 눌렀을 때 이미지가 바뀌는 코드이다.

![checkbox](https://bro-o.github.io/assets/images/random.PNG)

### HTML
```html
<!DOCTYPE html>
<head>
    <style>
        .wrapper {
            width: 500px;
            height: 500px;
            text-align: center;
        }
        #img {
            width: 100%;
            height: 100%;
        }
    </style>
    <link rel="stylesheet" href="food/style.css" />
</head>
<body>
    <div class="wrapper">
        <img id="img" src="../food/picture/1.jpg" />
        <button id="gen">Change</button>
    </div>
</body>
```

### JavaScript
```javascript
var genButton = document.getElementById('gen'); // Generate button

function genRandomMenu() {
	var number = Math.floor(Math.random() * 3) + 1;
	document.getElementById('img').src = '../food/picture/' + number + '.jpg';	   
}

genButton.addEventListener('click', genRandomMenu);
```

버튼에 EventListener를 추가하여 클릭 시 genRandomMenu 함수를 실행한다.
```
genButton.addEventListener('click', genRandomMenu);
```
랜덤으로 수를 발생시켜서 해당 번호의 이미지를 보여준다.
```
var number = Math.floor(Math.random() * 3) + 1;
	document.getElementById('img').src = '../food/picture/' + number + '.jpg';
```


