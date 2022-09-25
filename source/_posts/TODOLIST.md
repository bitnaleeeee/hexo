---
title: TO DO LIST
date: 2022-06-28 10:34
tags:
categories: jQuery
---

<h3>TO DO LIST 만들기</h3>

# 조건

1. 버튼을 클릭했을 때 작성한 내용이 할일로 추가 된다.
2. 엔터키를 눌렀을 때 버튼을 클릭한 것과 동일한 효과 적용
3. 작성된 리스트를 더블 클릭하면 밑줄이 그어진 후 서서히 삭제된다.
4. 입력창에 마우스 클릭 시 공란이 되게 한다.

## 구현

<style>
.sample .container {
  padding: 20px;
  width: 300px;
  margin: 0 auto;
  margin-top: 40px;
  background: white;
  border-radius: 5px;
}

.sample form {
  display: inline-block;
}

.sample input {
  padding: 4px 15px 4px 5px;
}

.sample #button {
  display: inline-block;
  background-color: #fc999b;
  color: #ffffff;
  border-radius: 5px;
  text-align: center;
  margin-top: 2px;
  padding: 5px 15px;
}

.sample #button:hover {
  cursor: pointer;
  opacity: .8;
}

.sample ol {
  padding-left: 20px;
}

.sample ol li {
  padding: 5px;
  color: #000;
}

.sample ol li:nth-child(even) {
  background: #dfdfdf;
}

.sample .strike {
  text-decoration: line-through;
}

.sample li:hover {
  cursor: pointer;
}
</style>
<div class="sample">
  <div class="container">
  <h2>Simple To Do List</h2>
  <p><em>Click and drag to reorder, double click to cross an item off.</em></p>

  <!-- <form name="toDoList"> -->

  <input type="text" name="ListItem" />

  <!-- </form> -->

  <div id="button">Add</div>
  <br />
  <ol></ol>
  </div>
<div>

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<link href="https://code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css" rel="stylesheet" type="text/css" />
<script type="text/javascript" src="https://code.jquery.com/jquery-1.12.4.min.js"></script>
<script type="text/javascript" src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
<script>
$(document).ready(function () {
  $('#button').click(function () {
    let toAdd = $('input[name=ListItem]').val(); $('.sample ol').append('<li>' + toAdd + '</li>');
  }); 
  $('input[name=ListItem]').keypress(function (e) {
    if (e.keyCode == 13) {
      $('#button').click();
        }
  }); 
  $(document).on('dblclick', 'li', function () {
    $(this).toggleClass('strike').fadeOut('slow');
    return false;
  }); $('input').focus(function () { $(this).val(''); }); 
  $('.sample ol').sortable();
});
</script>

```javascript
$(document).ready(function () {
  $("#button").click(function () {
    let toadd = $("input[name=ListItem]").val();
    $("ol").append("<li>" + toAdd + "</li>");
  });
  $("input[name=ListItem]").keyup(function (e) {
    if (e.keyCode == 13) {
      $("#button").click();
    }
  });
  $(document).on("dblclick", "li", function () {
    $(this).toggleClass("strike").fadeOut("slow");
    return false;
  });
  $("input").focus(function () {
    $(this).val("");
  });
  $("ol").sortable();
});
```

## 해설

1. ul 안에 li 요소가 추가된 경우 li를 선택하여 이벤트 코드를 작성할 경우 코드 이후에 작성된 li는 이벤트를 실행시키지 못하는 경우가 있으므로, 이런 경우 document를 선택하고 발생할 이벤트, 선택자를 작성해주면 해당 이벤트를 실행시킬 수 있다.
2. li에 (더블)클릭 이벤트를 작성해 줄 경우, 부모 태그 요소에도 이벤트가 적용되어 중복 실행될 수 있으므로 버블링을 방지하기 위해 return false를 작성해준다.
