---
title: jQuery Fixed Navigation UI
date: 2022-05-28 12:50:38
tags:
categories: jQuery
---

## UI 조건

1. 1.상단 메뉴바는 스크롤을 내려도 계속 상단에 노출된다.
2. 2.각 메뉴바를 누르면 첫 화면으로 올라간다.

## 구현

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<script>
$(document).ready(function() {
      $(window).scroll(function () {
        let height = $(document).scrollTop();
        let fixedNav = $('.fixedNav');
        if (height >= 300) {
          fixedNav.addClass('fixed');
        }
        else {
          fixedNav.removeClass('fixed');
        }
      })
    });

</script>
<style>
    * {
      margin: 0;
      padding: 0
    }
    html {
      height: 100%
    }
    body {
      height: 200%
    }
    ul li,
    ol li {
      list-style: none
    }
    .cnt {
      width: 100%;
      height: 300px;
      text-align: center;
      line-height: 300px;
      background-color: #ccc
    }
    .fixedNav {
      position: relative;
      box-shadow: 5px 5px 5px rgba(0, 0, 0, .2)
    }
    .fixedNav.fixed {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%
    }
    .fixedNav:after {
      content: '';
      display: block;
      clear: both
    }
    .fixedNav>li {
      float: left;
      width: 25%
    }
    .fixedNav>li>a {
      display: block;
      width: 100%;
      height: 50px;
      line-height: 50px;
      text-align: center;
      background-color: #333;
      color: #fff
    }
    .fixedNav>li>a:hover {
      background-color: #000
    }
</style>
  <script src="http://code.jquery.com/jquery-3.3.1.js"></script>
  <div class="cnt">contents</div>
  <ul class="fixedNav">
    <li><a href="#">link01</a></li>
    <li><a href="#">link02</a></li>
    <li><a href="#">link03</a></li>
    <li><a href="#">link04</a></li>
  </ul>
```javascript
window.onload = function(){

$(window).scroll(function () {
let height = $(document).scrollTop();
let fixedNav = $('.fixedNav');
if (height >= 300) {
fixedNav.addClass('fixed');
}
else {
fixedNav.removeClass('fixed');
}

      })

```
## 해설

1. 1.cnt의 hieght가 300이므로, widow.scrolltop이 300이 넘어갈 경우,
   해당 메뉴바를 상단(top=0)에 고정시키는 class를 입혀준다.
2. 2.만약 window.scrolltop이 300 이하인 경우, 메뉴바를 상단에
    고정시키게 되면, cnt보다 위에 있게 되므로 removeclass를 하여 적용을 해제시켜준다.

```
