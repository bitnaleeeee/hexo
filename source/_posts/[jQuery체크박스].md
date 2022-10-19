---
title: jQuery agree Checkbox UI
date: 2022-05-16 20:08:38
tags:
categories: jQuery
---

<h3>jQuery전체동의 체크박스 만들기</h3>

jQuery를 이용하여 전체동의 체크박스UI를 아래와 같이 만들어 보았다.

## 구현

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<script>
$(document).ready(function() {
    let agreeBox = $('label').find('input[type=checkbox]');
    let boxZero = agreeBox.eq(0);
    boxZero.on('click', function () {
        if (boxZero.prop('checked')) {
            agreeBox.prop('checked', true);
        }
        else {
            agreeBox.prop('checked', false);
        }
    })
    agreeBox.on('click', function () {
        let checkNum = 0;
        for (let i = 1; i < $('label').length; i++) {
            if (agreeBox.eq(i).prop('checked')) {
                checkNum++;
            }
        }
        console.log(checkNum);
        if (checkNum === 3) {
            boxZero.prop('checked', true)
        }
        else { boxZero.prop('checked', false) }
    })
});
</script>
<style>
* {
    margin: 0;
    padding: 0
}
#checkWrap {
    width: 120px
}
#checkWrap label {
    display: block;
    margin: 5px;
    font-size: 14px
}
#checkWrap label input[type="checkbox"] {
    margin-right: 5px;
    width: 20px;
    height: 20px;
    vertical-align: middle
}
#checkWrap label:first-child input[type="checkbox"] {
    width: 30px;
    height: 30px
}
</style>
<div id="checkWrap">
    <label for="cheeck01"><input type="checkbox" id="cheeck01" />전체 동의</label>
    <label for="cheeck02"><input type="checkbox" id="cheeck02" />동의</label>
    <label for="cheeck03"><input type="checkbox" id="cheeck03" />동의</label>
    <label for="cheeck04"><input type="checkbox" id="cheeck04" />동의</label>
</div>

```javascript
window.onload = function () {
  let agreeBox = $("label").find("input[type=checkbox]");
  let boxZero = agreeBox.eq(0);

  boxZero.on("click", function () {
    if (boxZero.prop("checked")) {
      agreeBox.prop("checked", true);
    } else {
      agreeBox.prop("checked", false);
    }
  });

  agreeBox.on("click", function () {
    let checkNum = 0;
    for (let i = 1; i < $("label").length; i++) {
      if (agreeBox.eq(i).prop("checked")) {
        checkNum++;
      }
    }
    console.log(checkNum);
    if (checkNum === 3) {
      boxZero.prop("checked", true);
    } else {
      boxZero.prop("checked", false);
    }
  });
};
```

<h2> 전체 동의 체크 박스 함수 만들기 </h2>

1. 전체동의 체크 박스를 클릭하면 모두 체크되고, 해제시 모두 해제되는 함수를 생성한다.
2. 해당 체크박스의 체크 유무를 알려주는 함수 prop를 이용하여 전체동의 체크박스에 체크가 되어있을 경우, 나머지 모든 체크박스의 porp chekced 값을 true 준다. (모든 체크박스 체크됨)
3. else, 전체동의 체크박스가 체크 되어 있지 않은 경우, 모든 체크박스 Prop의 checked 값을 false 로 주어 모두 해제 시킨다.

<h2> 동의 체크 박스에 따른 전체 동의 박스 체크 함수 만들기 </h2>

1. 포문을 이용하여 각 체크박스의 인덱스1 (즉 전체동의를 제외한 모든 체크박스)를 돌아가며, 체크가 되어있는지 확인한다.
2. 체크가 되어있을 경우, 임의로 만든 checknum 변수에 값을 1씩 더해준다.
3. 값이 3이 되었을때 (모든 동의체크박스가 체크 되어있을때), prop 함수를 이용하여 checked 값 true 를 주어 전체동의 박스를 체크한다.
4. else, 3의 값이 아닌 모든 경우, 전체동의 박스 체크를 해제한다. prop checked = false
