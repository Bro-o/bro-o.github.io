---
title: "Food Select App - 01 체크박스 카테고리"
layout: post
date: 2020-09-05 22:10
tag: 
-html
-css
headerImage: true
projects: true
hidden: true # don't count this post in blog pagination
description: "This is a simple and minimalist template for Jekyll."
category: project
author: Yun
externalLink: false
---


# 체크박스 카테고리
 
사용자가 카테고리를 선택하면 그에 해당하는 음식만 랜덤으로 보여주는 페이지를 만들기 위하여 체크박스 html을 추가하였다.

![checkbox](https://bro-o.github.io/assets/images/checkbox.PNG)
 
 
## html
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

 Css 참고 : https://codepen.io/design8383/pen/arHeC
 
## JavaScript

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

JavaScript 참고 : https://qja1998.github.io/2020-09-02-food-app/
    

