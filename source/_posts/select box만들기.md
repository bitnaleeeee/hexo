---
title: jQuery Select Box UI
date: 2022-04-21 20:37:08
tags:
categories: jQuery
---

## 조건

1. select class 클릭 시, list class 보이게 하라!
2. li 항목 클릭 시, 해당 텍스트가 select text에 담겨야 한다
3. li 항목 클릭 시, 형제 리스트 목록은 숨겨져야 한다. (클래스 제거)
4. list class가 보일때 select box를 제외한 부분을 클릭할 시, 모든 리스트는 숨겨져야 한다.

   조건 4-1. select 를 제외한 다른 부분을 클릭할때 = select 클릭이 아닐때
   조건 4-2. list가 다 보였을때

## 구현

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<script>
  $(document).ready(function () {
    $('.select').on('click', function () {
      $('.list').toggleClass('on');
    })

    $('li').on('click', function () {

      let pickList = $(this).text();
      $('.select').text(pickList);
      $(this).parent().removeClass('on');
    })
    $(document).on('click', function (event) {


      if (!($(event.target).is($('.select'))) && $('.list').hasClass('on')) {
        $('.list').removeClass('on')
      }
    })
  });
</script>

<style>
* {
margin: 0;
padding: 0;
}
.select_wrap {
margin: 20px;
}

.select_wrap .box {
display: inline-block;
position: relative;
width: 150px;
}

.select_wrap .box .select {
position: relative;
border: 2px solid #ccc;
box-sizing: border-box;
padding: 0 10px;
height: 40px;
line-height: 35px;
font-size: 16px;
background-color: #fff;
cursor: pointer;
}

.select_wrap .box .select:after {
content: '▼';
position: absolute;
top: 0;
right: 10px;
}

.select_wrap.on .box .select:after {
content: '▲';
}

.select_wrap .box .list {
display: none;
overflow-y: auto;
position: absolute;
top: 45px;
left: 0;
z-index: 10;
border: 2px solid #ccc;
box-sizing: border-box;
padding: 10px 0;
width: 100%;
max-height: 200px;
background-color: #fff;
}
.select_wrap .box .list.on {
display: block;
}
.select_wrap .box .list::-webkit-scrollbar {
width: 10px;
height: 0;
}

.select_wrap .box .list::-webkit-scrollbar-button:start:decrement,
.select_wrap .box .list::-webkit-scrollbar-button:end:increment {
display: block;
height: 0;
}

.select_wrap .box .list::-webkit-scrollbar-track {
background: rgba(0, 0, 0, .05);
-webkit-border-radius: 10px;
border-radius: 10px;
}

.select_wrap .box .list::-webkit-scrollbar-thumb {
height: 50px;
width: 50px;
background: rgba(0, 0, 0, .2);
-webkit-border-radius: 5px;
border-radius: 5px;
}

.select_wrap .box .list>li {
box-sizing: border-box;
padding: 0 10px;
width: 100%;
height: 35px;
line-height: 35px;
cursor: pointer;
}

.select_wrap .box .list>li:hover {
background-color: #ccc;
}
</style>

<div class="select_wrap">
  <div class="box">
    <div class="select">먹고싶은 과일</div>
    <ul class="list">
      <li class="selected">선택</li>
      <li>딸기</li>
      <li>귤</li>
      <li>오렌지</li>
      <li>블루베리</li>
      <li>파인애플</li>
      <li>망고</li>
      <li>스테비아토마토</li>
      <li>메론</li>
      <li>바나나</li>
      <li>체리</li>
    </ul>
  </div>
</div>

```javascript
$(document).ready(function()

    $('.select').on('click', function() {
          $('.list').toggleClass('on');
          })

    $('li').on('click', function() {

      let pickList = $(this).text();
      $('.select').text(pickList);
      $(this).parent().removeClass('on');
    })


      $(document).on('click', function(event) {


        if(!($(event.target).is($('.select'))) && $('.list').hasClass('on')){
          $('.list').removeClass('on')
        }

      })
};

```

## 해설

1. toggleClass('클래스명') 함수는 클릭할때 해당 클래스가 적용되고, 다시 한번 클릭하면 자동 해제된다.
2. $('객체').text()는 해당 객체의 텍스트를 저장한다. text 괄호 ()안에 값을 넣으면, 해당 객체안의 텍스트에 값이 들어간다.
3. event.target();은 클릭한 객체를 나타낸다. event.target.is();는 ()안에 해당 값이 들어가있으면 true, 아닐시 false를 반환한다.
4. hasClass('클래스명')함수는 해당 클래스가 있을시 true, 없을시 false를 반환한다.
