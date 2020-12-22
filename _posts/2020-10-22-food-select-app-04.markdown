---
title: "Food Select App - 04 사이드 메뉴"
layout: post
date: 2020-10-22 22:10
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

# 4. 사이드 메뉴
## 사이드바
오른쪽 위에 있는 버튼을 누르면 사이드바가 보였다가, 사이드바의 화살표를 누르면 다시 사라지게 했다.
### JavaScript(Slide bar)
```javascript
<script>
    var menu = document.getElementById('cbp-spmenu-s2'),
        show = document.getElementById('home'),
        disable = document.getElementById('diasble');

    show.onclick = function () {
        classie.toggle(this, 'active');
        classie.toggle(menu, 'cbp-spmenu-open');
        disableOther('show');
    };
    disable.onclick = function () {
        classie.toggle(this, 'active');
        classie.toggle(menu, 'cbp-spmenu-open');
        disableOther('show');
    };
    function disableOther(button) {
        if (button !== 'show') {
            classie.toggle(show, 'disabled');
        }
    }
</script>
```
toggle을 이용하여 보였다가 사라지게 할 수 있도록 했다.

![checkbox](https://bro-o.github.io/assets/images/sidebar.png)

## 사이드 메뉴
change 버튼 옆에 있는 카트 모양의 버튼을 누르게 되면 사이드바에 현재 이미지가 저장되고, X 버튼을 누르면 삭제된다.
### JavaScript(Side Menu)
```javascript
<script>
    const cartBtn = document.querySelectorAll('.cart-button');
    
    ...
    
        cartBtn.forEach(function (btn) {
            btn.addEventListener('click', function (event) {
                if (event.target.parentElement.classList.contains("cart-button")) {
                    
                    ...

                    const cartItem = document.createElement('div');
                    cartItem.classList.add("cart-item");
                    cartItem.setAttribute('id', 'cart-item' + partNum[0]);

                    cartItem.innerHTML = '<img src="image src" ... /> <button type="button" ... onClick="remove()"/></button> ';

                    ...

                    //select cart
                    const cart = document.getElementById("cart");
                    const end = document.getElementById("end");

                    cart.insertBefore(cartItem, end);
                }
            });
        });

        function remove() {
            var btnID = event.srcElement.id;
            var partNum = btnID.split('/');
            var cart = document.getElementById("cart-item/" + partNum[1]);
            
            ...
            
            cart.remove(cart);
            
            ...
        }
    </script>
```
현재 나와있는 이미지 주소로 부터 이미지 번호만 추출하여 innerhtml로 새로운 html을 생성하여 사이드바에 넣는다. remove를 이용하여 삭제할 수도 있다.
```
cartItem.innerHTML = '';
...
cart.insertBefore(cartItem, end);
...
cart.remove(cart);
```
![checkbox](https://bro-o.github.io/assets/images/sidemenu.png)

## Toast 알림
### JavaScript (toast)
```javascript
<script>
    function toast(string) {
        const toast = document.getElementById("toast");

        toast.classList.contains("reveal") ?
            (clearTimeout(removeToast), removeToast = setTimeout(function () {
                document.getElementById("toast").classList.remove("reveal")
            }, 1000)) :
            removeToast = setTimeout(function () {
                document.getElementById("toast").classList.remove("reveal")
            }, 1000)
        toast.classList.add("reveal"),
            toast.innerText = string
    }
    
    //popup 실행
    toast('추가 완료!');
    toast('삭제 완료!');
</script>
```
![checkbox](https://bro-o.github.io/assets/images/toast.png)

