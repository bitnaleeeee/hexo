---
title: jQuery hamburger menu UI
date: 2022-05-28 12:50:38
tags:
categories: jQuery
---

## UI 조건

1. 햄버거 메뉴 버튼 클릭시, 각기 다른 클래스가 입혀진다.
2. 다시 클릭시 기존 햄버거 메뉴로 돌아온다.

## 구현

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<script>
$(document).ready(function() {
     $('.menu-trigger').each(function (index) {
        $(this).on('click', function (e) {
          e.preventDefault();
          $(this).addClass('active-' + (index + 1));
        })
      });
    });

</script>
<style>
   body {
      background-color: #333;
      width: 500px;
      margin: 30px auto;
    }
    .menu-trigger {
      margin-right: 70px;
      margin-bottom: 50px;
    }
    .menu-trigger,
    .menu-trigger span {
      display: inline-block;
      transition: all .4s;
      box-sizing: border-box;
    }
    .menu-trigger {
      position: relative;
      width: 50px;
      height: 44px;
    }
    .menu-trigger span {
      position: absolute;
      left: 0;
      width: 100%;
      height: 4px;
      background-color: #fff;
      border-radius: 4px;
    }
    .menu-trigger span:nth-of-type(1) {
      top: 0;
    }
    .menu-trigger span:nth-of-type(2) {
      top: 20px;
    }
    .menu-trigger span:nth-of-type(3) {
      bottom: 0;
    }
    /* type-01 */
    /* 중앙 라인이 고정된 자리에서 투명하게 사라지며 상하라인 회전하며 엑스자 만들기 */
    .menu-trigger.active-1 span:nth-of-type(1) {
      -webkit-transform: translateY (20px) rotate (-45deg);
      transform: translateY(20px) rotate(-45deg);
    }
    .menu-trigger.active-1 span:nth-of-type(2) {
      opacity: 0;
    }
    .menu-trigger.active-1 span:nth-of-type(3) {
      -webkit-transform: translateY(-20px) rotate(45deg);
      transform: translateY(-20px) rotate(45deg);
    }
    /* type-02 */
    /* 중앙 라인이 고정된 자리에서 투명하게 사라지며 상하라인  회전하며 엑스자 만들기 */
    .menu-trigger.active-2 span:nth-of-type(1) {
      -webkit-transform: translateY(20px) rotate(-315deg);
      transform: translateY(20px) rotate(-315deg);
    }
    .menu-trigger.active-2 span:nth-of-type(2) {
      opacity: 0;
    }
    .menu-trigger.active-2 span:nth-of-type(3) {
      -webkit-transform: translateY(-20px) rotate(315deg);
      transform: translateY(-20px) rotate(315deg);
    }
    /* type-03 */
    /* 메뉴 전체가 회전하면서 엑스자 버튼 만들기 */
    .menu-trigger.active-3 {
      -webkit-transform: rotate(360deg);
      transform: rotate(360deg);
    }
    .menu-trigger.active-3 span:nth-of-type(1) {
      -webkit-transform: translateY(20px) rotate(-45deg);
      transform: translateY(20px) rotate(-45deg);
    }
    .menu-trigger.active-3 span:nth-of-type(2) {
      -webkit-transform: translateY(0) rotate(45deg);
      transform: translateY(0) rotate(45deg);
    }
    .menu-trigger.active-3 span:nth-of-type(3) {
      opacity: 0;
    }
    /* type-04 */
    /* 메뉴 전체가 회전하면서 엑스자 버튼 만들기 #2 */
    .menu-trigger span.nthtype-04,
    .menu-trigger.active-4 span:nth-of-type(3) {
      transition: none;
    }
    .menu-trigger.active-4 {
      -webkit-transform: rotateX(720deg);
      transform: rotateX(720deg);
    }
    .menu-trigger.active-4 span:nth-of-type(1) {
      -webkit-transform: translateY(20px) rotate(-45deg);
      transform: translateY(20px) rotate(-45deg);
    }
    .menu-trigger.active-4 span:nth-of-type(2) {
      -webkit-transform: translateY(0) rotate(45deg);
      transform: translateY(0) rotate(45deg);
    }
    .menu-trigger.active-4 span:nth-of-type(3) {
      opacity: 0;
    }
    /* type-05 */
    /* 중앙 라인이 밖으로 빠지면서 상하라인 엑스자 만들기 */
    .menu-trigger.active-5 span:nth-of-type(1) {
      -webkit-transform: translateY(20px) rotate(-45deg);
      transform: translateY(20px) rotate(-45deg);
    }
    .menu-trigger.active-5 span:nth-of-type(2) {
      left: 50%;
      opacity: 0;
      -webkit-animation: active-menu-bar05 .8s forwards;
      animation: active-menu-bar05 .8s forwards;
    }
    @-webkit-keyframes active-menu-bar05 {
      100% {
        height: 0;
      }
    }
    @keyframes active-menu-bar05 {
      100% {
        height: 0;
      }
    }
    .menu-trigger.active-5 span:nth-of-type(3) {
      -webkit-transform: translateY(-20px) rotate(45deg);
      transform: translateY(-20px) rotate(45deg);
    }
    /* type-06 */
    /* 중앙 라인이 밖으로 멀리 날아가듯 빠지면서 상하라인 엑스자 만들기 */
    .menu-trigger.active-6 span:nth-of-type(1) {
      -webkit-transform: translateY(20px) rotate(-45deg);
      transform: translateY(20px) rotate(-45deg);
    }
    .menu-trigger.active-6 span:nth-of-type(2) {
      left: 200%;
      opacity: 0;
      -webkit-transform: translateY(10px);
      transform: translateY(10px);
      -webkit-animation: active-menu-bar06 .8s forwards;
      animation: active-menu-bar06 .8s forwards;
    }
    @-webkit-keyframes active-menu-bar06 {
      100% {
        height: 0;
      }
    }
    @keyframes active-menu-bar06 {
      100% {
        height: 0;
      }
    }
    .menu-trigger.active-6 span:nth-of-type(3) {
      -webkit-transform: translateY(-20px) rotate(45deg);
      transform: translateY(-20px) rotate(45deg);
    }
    /* type-07 */
    /* 라인이 하나로 합쳐졌다가 엑스자 만들기 */
    .menu-trigger.type7 span:nth-of-type(1) {
      -webkit-animation: menu-bar07-01 .75s forwards;
      animation: menu-bar07-01 .75s forwards;
    }
    @-webkit-keyframes menu-bar07-01 {
      0% {
        -webkit-transform: translateY(20px) rotate(45deg);
      }
      50% {
        -webkit-transform: translateY(20px) rotate(0);
      }
      100% {
        -webkit-transform: translateY(0) rotate(0);
      }
    }
    @keyframes menu-bar07-01 {
      0% {
        transform: translateY(20px) rotate(45deg);
      }
      50% {
        transform: translateY(20px) rotate(0);
      }
      100% {
        transform: translateY(0) rotate(0);
      }
    }
    .menu-trigger.type7 span:nth-of-type(2) {
      transition: all .25s .25s;
      opacity: 1;
    }
    .menu-trigger.type7 span:nth-of-type(3) {
      -webkit-animation: menu-bar07-02 .75s forwards;
      animation: menu-bar07-02 .75s forwards;
    }
    @-webkit-keyframes menu-bar07-02 {
      0% {
        -webkit-transform: translateY(-20px) rotate(-45deg);
      }
      50% {
        -webkit-transform: translateY(-20px) rotate(0);
      }
      100% {
        -webkit-transform: translateY(0) rotate(0);
      }
    }
    @keyframes menu-bar07-02 {
      0% {
        transform: translateY(-20px) rotate(-45deg);
      }
      50% {
        transform: translateY(-20px) rotate(0);
      }
      100% {
        transform: translateY(0) rotate(0);
      }
    }
    .menu-trigger.active-7 span:nth-of-type(1) {
      -webkit-animation: active-menu-bar07-01 .75s forwards;
      animation: active-menu-bar07-01 .75s forwards;
    }
    @-webkit-keyframes active-menu-bar07-01 {
      0% {
        -webkit-transform: translateY(0) rotate(0);
      }
      50% {
        -webkit-transform: translateY(20px) rotate(0);
      }
      100% {
        -webkit-transform: translateY(20px) rotate(45deg);
      }
    }
    @keyframes active-menu-bar07-01 {
      0% {
        transform: translateY(0) rotate(0);
      }
      50% {
        transform: translateY(20px) rotate(0);
      }
      100% {
        transform: translateY(20px) rotate(45deg);
      }
    }
    .menu-trigger.active-7 span:nth-of-type(2) {
      opacity: 0;
    }
    .menu-trigger.active-7 span:nth-of-type(3) {
      -webkit-animation: active-menu-bar07-02 .75s forwards;
      animation: active-menu-bar07-02 .75s forwards;
    }
    @-webkit-keyframes active-menu-bar07-02 {
      0% {
        -webkit-transform: translateY(0) rotate(0);
      }
      50% {
        -webkit-transform: translateY(-20px) rotate(0);
      }
      100% {
        -webkit-transform: translateY(-20px) rotate(-45deg);
      }
    }
    @keyframes active-menu-bar07-02 {
      0% {
        transform: translateY(0) rotate(0);
      }
      50% {
        transform: translateY(-20px) rotate(0);
      }
      100% {
        transform: translateY(-20px) rotate(-45deg);
      }
    }
    /* type-08 */
    /* 상하라인이 움직여 화살표 만들기 */
    .menu-trigger.active-8 span:nth-of-type(1),
    .menu-trigger.active-8 span:nth-of-type(3) {
      width: 20px;
    }
    .menu-trigger.active-8 span:nth-of-type(1) {
      -webkit-transform: translate(-1px, 13px) rotate(-45deg);
      transform: translate(-1px, 13px) rotate(-45deg);
    }
    .menu-trigger.active-8 span:nth-of-type(3) {
      -webkit-transform: translate(-1px, -13px) rotate(45deg);
      transform: translate(-1px, -13px) rotate(45deg);
    }
    /* type-09 */
    /* 전체가 회전하며 화살표 만들기 */
    .menu-trigger.active-9 {
      -webkit-transform: rotate(360deg);
      transform: rotate(360deg);
    }
    .menu-trigger.active-9 span:nth-of-type(1),
    .menu-trigger.active-9 span:nth-of-type(3) {
      width: 20px;
    }
    .menu-trigger.active-9 span:nth-of-type(1) {
      -webkit-transform: translate(-1px, 13px) rotate(-45deg);
      transform: translate(-1px, 13px) rotate(-45deg);
    }
    .menu-trigger.active-9 span:nth-of-type(3) {
      -webkit-transform: translate(-1px, -13px) rotate(45deg);
      transform: translate(-1px, -13px) rotate(45deg);
    }
    /* type-10 */
    /* 메뉴 버튼이 세로로 회전하기 */
    .menu-trigger.active-10 {
      -webkit-transform: rotate(90deg);
      transform: rotate(90deg);
    }
    /* type-11 */
    /* 전체 메뉴를 감싸는 원 파형이 살며시 퍼지며 엑스버튼 만들기 */
    .menu-trigger span.type11:nth-of-type(1) {
      -webkit-animation: menu-bar11-01 .5s forwards;
      animation: menu-bar11-01 .5s forwards;
    }
    @-webkit-keyframes menu-bar11-01 {
      0% {
        -webkit-transform: translateY(20px) rotate(-45deg);
      }
      100% {
        -webkit-transform: translateY(0) rotate(0deg);
      }
    }
    @keyframes menu-bar11-01 {
      0% {
        transform: translateY(20px) rotate(-45deg);
      }
      100% {
        transform: translateY(0) rotate(0deg);
      }
    }
    .menu-trigger span.type11:nth-of-type(2) {
      -webkit-animation: menu-bar11-02 .5s forwards;
      animation: menu-bar11-02 .5s forwards;
    }
    @-webkit-keyframes menu-bar11-02 {
      0% {
        opacity: 0;
      }
      100% {
        opacity: 1;
      }
    }
    @keyframes menu-bar11-02 {
      0% {
        opacity: 0;
      }
      100% {
        opacity: 1;
      }
    }
    .menu-trigger span.type11:nth-of-type(3) {
      -webkit-animation: menu-bar11-03 .5s forwards;
      animation: menu-bar11-03 .5s forwards;
    }
    @-webkit-keyframes menu-bar11-03 {
      0% {
        -webkit-transform: translateY(-20px) rotate(45deg);
      }
      100% {
        -webkit-transform: translateY(0) rotate(0deg);
      }
    }
    @keyframes menu-bar11-03 {
      0% {
        transform: translateY(-20px) rotate(45deg);
      }
      100% {
        transform: translateY(0) rotate(0deg);
      }
    }
    .menu-trigger.type11:after {
      position: absolute;
      top: 50%;
      left: 50%;
      display: block;
      content: '';
      width: 30px;
      height: 30px;
      margin: -16px 0 0 -16px;
      border-radius: 50%;
      border: 1px solid rgba(255, 255, 255, 0.3);
      transition: all .1s;
      opacity: 0;
    }
    .menu-trigger.active-11:after {
      -webkit-animation: circle .5s;
      animation: circle .5s;
    }
    @-webkit-keyframes circle {
      0% {
        -webkit-transform: scale(0.1);
        opacity: 0;
      }
      50% {
        opacity: 1;
      }
      100% {
        -webkit-transform: scale(3.5);
        opacity: 0;
      }
    }
    @keyframes circle {
      0% {
        transform: scale(0.1);
        opacity: 0;
      }
      50% {
        opacity: 1;
      }
      100% {
        transform: scale(3.5);
        opacity: 0;
      }
    }
    .menu-trigger.active-11 span:nth-of-type(1) {
      -webkit-animation: active-menu-bar11-01 .5s .5s forwards;
      animation: active-menu-bar11-01 .5s .5s forwards;
    }
    @-webkit-keyframes active-menu-bar11-01 {
      0% {
        -webkit-transform: translateY(0) rotate(0deg);
      }
      100% {
        -webkit-transform: translateY(20px) rotate(-45deg);
      }
    }
    @keyframes active-menu-bar11-01 {
      0% {
        transform: translateY(0) rotate(0deg);
      }
      100% {
        transform: translateY(20px) rotate(-45deg);
      }
    }
    .menu-trigger.active-11 span:nth-of-type(2) {
      -webkit-animation: active-menu-bar11-02 .5s .5s forwards;
      animation: active-menu-bar11-02 .5s .5s forwards;
    }
    @-webkit-keyframes active-menu-bar11-02 {
      0% {
        opacity: 1;
      }
      100% {
        opacity: 0;
      }
    }
    @keyframes active-menu-bar11-02 {
      0% {
        opacity: 1;
      }
      100% {
        opacity: 0;
      }
    }
    .menu-trigger.active-11 span:nth-of-type(3) {
      -webkit-animation: active-menu-bar11-03 .5s .5s forwards;
      animation: active-menu-bar11-03 .5s .5s forwards;
    }
    @-webkit-keyframes active-menu-bar11-03 {
      0% {
        -webkit-transform: translateY(0) rotate(0deg);
      }
      100% {
        -webkit-transform: translateY(-20px) rotate(45deg);
      }
    }
    @keyframes active-menu-bar11-03 {
      0% {
        transform: translateY(0) rotate(0deg);
      }
      100% {
        transform: translateY(-20px) rotate(45deg);
      }
    }
    /* type-12 */
    /* 메뉴 전체를 감싸는 원형을 만들면서 엑스자버튼 만들기 */
    .menu-trigger.type12:after {
      position: absolute;
      top: 50%;
      left: 50%;
      display: block;
      content: '';
      width: 84px;
      height: 84px;
      margin: -45px 0 0 -45px;
      border-radius: 50%;
      border: 4px solid transparent;
      transition: all .75s;
    }
    .menu-trigger.active-12 span:nth-of-type(1) {
      -webkit-transform: translateY(20px) rotate(-45deg);
      transform: translateY(20px) rotate(-45deg);
    }
    .menu-trigger.active-12 span:nth-of-type(2) {
      left: 60%;
      opacity: 0;
      -webkit-animation: active-menu-bar12-01 .8s forwards;
      animation: active-menu-bar12-01 .8s forwards;
    }
    @-webkit-keyframes active-menu-bar12-01 {
      100% {
        height: 0;
      }
    }
    @keyframes active-menu-bar12-01 {
      100% {
        height: 0;
      }
    }
    .menu-trigger.active-12 span:nth-of-type(3) {
      -webkit-transform: translateY(-20px) rotate(45deg);
      transform: translateY(-20px) rotate(45deg);
    }
    .menu-trigger.active-12:after {
      -webkit-animation: circle-12 .4s .25s forwards;
      animation: circle-12 .4s .25s forwards;
    }
    @-webkit-keyframes circle-12 {
      0% {
        border-color: transparent;
        -webkit-transform: rotate(0deg);
      }
      25% {
        border-color: transparent #fff transparent transparent;
      }
      50% {
        border-color: transparent #fff #fff transparent;
      }
      75% {
        border-color: transparent #fff #fff #fff;
      }
      100% {
        border-color: #fff;
        -webkit-transform: rotate(-680deg);
      }
    }
    @keyframes circle-12 {
      0% {
        border-color: transparent;
        transform: rotate (0deg);
      }
      25% {
        border-color: transparent #fff transparent transparent;
      }
      50% {
        border-color: transparent #fff #fff transparent;
      }
      75% {
        border-color: transparent #fff #fff #fff;
      }
      100% {
        border-color: #fff;
        transform: rotate (-680deg);
      }
    }
</style>
  <script src="http://code.jquery.com/jquery-3.3.1.js"></script>
   <a class="menu-trigger" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger" href="#">
    <span></span>
    <span></span>
    <span class="nthtype-04"></span>
  </a>

  <a class="menu-trigger" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger type7" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger type11" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

  <a class="menu-trigger type12" href="#">
    <span></span>
    <span></span>
    <span></span>
  </a>

```javascript
window.onload = function () {
  $(".menu-trigger").each(function (index) {
    $(this).on("click", function (e) {
      e.preventDefault();
      $(this).addClass("active-" + (index + 1));
    });
  });
};
```

## 해설

1. 각 menu trigger 클래스 안의 12개 요소를 선택해주는 함수를 작성한다.
2. this로 총 12개의 menu-trigger를 받고 하나씩 클릭할때마다 각 index값의 1을 더해준 active-(index+1)명의 클래스를 입혀준다.
3. 재클릭시 원래 모양으로 복귀해야하므로 toggleclass를 사용.
4. preventDefault();는 a태그가 실행되지 않도록 막아준다.
