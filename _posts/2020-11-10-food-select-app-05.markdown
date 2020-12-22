---
title: "Food Select App - 05 장바구니"
layout: post
date: 2020-11-10 22:10
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

# 5. 장바구니
사이드 메뉴에 저장했던 음식들을 한눈에 볼 수 있도록 장바구니 페이지를 만들었다.
```javascript
<script>
    var locationNum = location.href.split('&');
    var tmp = locationNum[0].split('?');
    var itemNum = tmp[1].split('/');

    for (var i = 1; i < itemNum.length; i++) {

        const item = {};

        item.img = "../picture/" + itemNum[i] + ".png";
        console.log(item);

        const basketItem = document.createElement('div');
        basketItem.classList.add("basket-item");
        basketItem.setAttribute('id', 'basket-item' + itemNum[i]);

        basketItem.innerHTML = '<img src=' + item.img + ' class="basket-image" id="basket-image"/> <button id="basket-item-remove/' + itemNum[i] + '" type="button" class="basket-item-remove" onClick="remove()"> <img id="cart-item-remove/' + itemNum[i] + '" class="remove-img" src="../picture/remove.png"/></button>';
            
        //select cart
        const basket = document.getElementById("basket");
        const end = document.getElementById("end");

        basket.insertBefore(basketItem, end);
    }
</script>
```
![checkbox](https://bro-o.github.io/assets/images/cart.png)
