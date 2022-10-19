---
title: jQuery modal window UI
date: 2022-04-01 12:50:38
tags:
categories: jQuery
---

## UI 조건

1. 눌러보세용 클릭 시 모달 창이 나타난다.
2. 닫기를 누르면 모달창이 닫아진다.

## 구현

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<script>
$(document).ready(function() {
      $('.modalLink').on('click', function () {
        $('#modalLayer').fadeIn('slow');
        $('.modalContent').css({ "margin-top": "-220px", "margin-left": "-100px" });
        $(this).blur();
        $('.modalContent > a').focus();
        return false;
      });
      $('button').on('click', function () {
        $('#modalLayer').fadeOut('slow')
        $('.modalLink').focus();
      })
    });


</script>
<style>
      a {
      color: #000;
    }
    .mask {
      width: 100%;
      height: 100%;
      position: fixed;
      left: 0;
      top: 0;
      z-index: 10;
      background: #000;
      opacity: .5;
      filter: alpha(opacity=50);
    }
    #modalLayer {
      display: none;
      position: relative;
    }
    #modalLayer .modalContent {
      width: 440px;
      height: 200px;
      padding: 20px;
      border: 1px solid #ccc;
      position: fixed;
      left: 50%;
      top: 50%;
      z-index: 11;
      background: #fff;
    }
    #modalLayer .modalContent button {
      position: absolute;
      right: 0;
      top: 0;
      cursor: pointer;
    }
</style>
  <script src="http://code.jquery.com/jquery-3.3.1.js"></script>

<a href="#modalLayer" class="modalLink">눌러보세용</a>

  <div id="modalLayer">
    <div class="modalContent">
      <a href="#">모달창 테스트</a>
      <button type="button">닫기</button>
    </div>
  </div>

```javascript
$(document).ready(function () {
  $(".modalLink").on("click", function () {
    $("#modalLayer").fadeIn("slow");
    $(".modalContent").css({ "margin-top": "-220px", "margin-left": "-100px" });
    $(this).blur();
    $(".modalContent > a").focus();
    return false;
  });

  $("button").on("click", function () {
    $("#modalLayer").fadeOut("slow");
    $(".modalLink").focus();
  });
});
```

## 해설

1. retrun false는 함수를 중복 실행되지 않게 방지한다(이벤트 실행방지)
2. focus 와 blur 를 사용하여 버블링 및 캡쳐링 모두 발생되지 않게 한다.
