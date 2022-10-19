---
title: jQuery Slide banner UI
date: 2022-05-25 21:08:51
tags:
categories: jQuery
---

## 구현

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<script>
  $(document).ready(function () {
     load();


$('.btn .prev').on('click', function () {

        prev();

      }) 
      $('.btn .next').on('click', function () {
        
        next();

      })

      function load() {

        $('.slide .slideCnt li').not(":first").css("left", "800px");
      }

      let num = 0;

      function prev() {
        $('.slide .slideCnt li').eq(num).css("left", "800px");
        num--;
        if (num < 0) { num = 3; }

        $('.slide .slideCnt li').eq(num).animate({ left: "0px" }, 500);

      }

      function next() {
        $('.slide .slideCnt li').eq(num).css("left", "800px");
        num++;
        if (num > 3) { num = 0; }
        $('.slide .slideCnt li').eq(num).animate({ left: "0px" }, 500);


      }


  });
</script>

 <style>
    * {
      margin: 0;
      padding: 0
    }

    .slide {
      position: relative;
      margin: 0 auto;
      width: 800px;
      height: 500px;
      text-align: center
    }

    .slide .slideCnt {
      position: relative;
      overflow: hidden;
      width: 800px;
      height: 500px;

    }

    .slide .slideCnt li {
      position: absolute;
      ;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      list-style: none;
      font-size: 50px;
      line-height: 500px;
      text-align: center;
      color: #fff
    }

    .slide .slideCnt li:nth-child(1) {
      background-color: #ccc
    }

    .slide .slideCnt li:nth-child(2) {
      background-color: #999
    }

    .slide .slideCnt li:nth-child(3) {
      background-color: #666
    }

    .slide .slideCnt li:nth-child(4) {
      background-color: #333
    }

    .slide .btn a {
      position: absolute;
      top: 50%;
      margin-top: -15px;
      border-radius: 3px;
      width: 50px;
      height: 30px;
      text-align: center;
      text-decoration: none;
      line-height: 30px;
      background-color: #fff;
      color: #333
    }

    .slide .btn a.prev {
      left: 10px
    }

    .slide .btn a.next {
      right: 10px
    }

    .slide .indicator {
      display: inline-block;
      position: relative;
      bottom: 30px
    }

    .slide .indicator a {
      display: block;
      float: left;
      margin-left: 5px;
      border-radius: 3px;
      width: 20px;
      height: 20px;
      text-align: center;
      text-decoration: none;
      line-height: 20px;
      background-color: #fff;
      color: #333
    }

    .slide .indicator a:first-child {
      margin-left: 0
    }

    .slide .indicator a.on {
      background-color: #000;
      color: #fff
    }

    .slide .autoBtn {
      position: absolute;
      bottom: 10px;
      right: 10px;
      border-radius: 3px;
      width: 50px;
      height: 30px;
      text-align: center;
      text-decoration: none;
      line-height: 30px;
      background-color: #fff;
      color: #333
    }
  </style>
</head>

<body>
  <div class="slide">
    <ul class="slideCnt">
      <li>slide1</li>
      <li>slide2</li>
      <li>slide3</li>
      <li>slide4</li>
    </ul>
    <div class="btn">
      <a href="#" class="prev">prev</a>
      <a href="#" class="next">next</a>
    </div>
  </div>
</body>

</html>

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
