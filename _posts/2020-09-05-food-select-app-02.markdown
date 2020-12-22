---
title: "Food Select App - 02 체크박스 카테고리"
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

# 2. 체크박스 카테고리
 
사용자가 카테고리를 선택하면 그에 해당하는 음식만 랜덤으로 보여주는 페이지를 만들기 위하여 체크박스 html을 추가하였다.

![checkbox](https://bro-o.github.io/assets/images/checkbox.PNG)
 
 
### HTML
```html
<html>
	<head>
	    <link rel="stylesheet" href="boxStyle.css" />
	</head>
	<body>
	    <div class="container">
	        <section class="todo">
	            <ul class="todo-list">
	                <li>
	                    <input type="checkbox" id="han" />
	                    <label class="toggle" for="han"></label>
	                    한식
	                </li>
	                <li>
	                    <input type="checkbox" id="boon" value="2" />
	                    <label class="toggle" for="boon"></label>
	                    분식
	                </li>
	                <li>
	                    <input type="checkbox" id="joong" />
	                    <label class="toggle" for="joong"></label>
	                    중식
	                </li>
	                <li>
	                    <input type="checkbox" id="il" />
	                    <label class="toggle" for="il"></label>
	                    일식
	                </li>
	                <li>
	                    <input type="checkbox" id="yang" />
	                    <label class="toggle" for="yang"></label>
	                    양식
	                </li>
	            </ul>
	            <ul class="todo-pagination">
	                <button id="next">Next</button>
	            </ul>
	        </section>
         </div>
     </body>
 <html>
```
    
 Css 참고 : https://codepen.io/design8383/pen/arHeC

 ### JavaScript (check box)
 해당 카테고리를 랜덤 페이지에 넘기는 코드
```javascript
<script>
    var nextButton = document.getElementById('next');

    var arrChk = new Array();

    var num = '';

    arrChk[0] = document.getElementById('han');
    arrChk[1] = document.getElementById('boon');
    arrChk[2] = document.getElementById('joong');
    arrChk[3] = document.getElementById('il');
    arrChk[4] = document.getElementById('yang');

    function changepage() {
        for (var i = 0; i < 5; i++) {
            if (arrChk[i].checked) {
                var n = i + 1;
                num = num + n;
            } else continue;
        }
        window.location.href = 'random.html?' + num;
    }

    nextButton.addEventListener('click', changepage);
</script>
```
**if문**을 이용하여 체크된 카테고리만 num에 문자열로 저장한다. 체크여부는 **boolean**으로 확인할 수 있다.
```
if (arrChk[i].checked)
```
주소에 num 값을 추가하여 random.html로 넘겨 준다.
```
window.location.href = 'random.html?' + num;
```
 ---

### JavaScript (random)
```javascript
	var genButton = document.getElementById('gen'); // Generate button
	var tmp = location.href.split('?');
	var codeNum = String(tmp[1]);

	function genRandomMenu() {
	    var picCode = "";
	    while (true) {
	        var number = String(Math.floor(Math.random() * 3) + 1);
	        if (codeNum.indexOf(number)!=-1) {
	            picCode = number + String(Math.floor(Math.random() * 3));
	            break;
	        } else continue;
	    }
	    document.getElementById('img').src = '../food/picture/' + picCode + '.png';
	}
					
	genButton.addEventListener('click', genRandomMenu);
```
주소를 '**?**'를 기준으로 나눠서 checkbox에서 넘겨준 코드를 codeNum에 저장한다.
```
var tmp = location.href.split('?');
var codeNum = String(tmp[1]);
```
카테고리, 사진번호. 두 번의 난수를 생성하여 하나의 코드를 만들어준다. 여기서 앞자리는 카테고리, 뒷자리는 사진번호이다. 예를 들어 '**31**'이면 3은 세번째 카테고리인 중식, 1은 중식 사진 중 첫번째 사진을 나타낸다. 이미지를 저장할 때도 이 규칙대로 저장한다.
```
var picCode = "";
while (true) {
	var number = String(Math.floor(Math.random() * 3) + 1);
	if (codeNum.indexOf(number)!=-1) {
	    picCode = number + String(Math.floor(Math.random() * 3));
	    break;
	} else continue;
```
