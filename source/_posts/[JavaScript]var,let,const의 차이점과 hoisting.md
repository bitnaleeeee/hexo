---
title: var,let,const의 차이점과 hoisting
date: 2022-09-17 16:54:00
tags: hoisting
categories: javascript
---

## 변수 선언 var, let const의 차이

변수를 선언할 때 var, let, const 로 할 수 있다. var 는 초창기 문법이고 ES6에서 let과 const가 추가 되었다. var의 경우 재선언, 재할당을 할 수 있으며 let은 재할당은 가능하나, 재선언은 불가능하다. const는 재선언, 재할당이 모두 불가능하다. 따라서 var의 경우 재선언이 가능하므로 변수명 중복 등 개발자 입장에서 error prone해지며 지양해야하는 코드라고 볼 수 있다.

또한 var의 경우 block scope밖에서 접근이 가능하지만(함수 제외, if문과 for문 등에서 접근 가능하다.) let과 const는 block scope 밖에서 접근이 불가능하다. 이제 var, let const를 hoisitng과 연관지어 차이점을 알아보자.

## hoistig이란?

hoisitng은 함수 선언식과 변수선언이 최상단에 끌어올려지는 것을 말한다. hoisitng는 JS 동작 그 자체이며, 자바스크립트 엔진은 함수선언문 > 변수 선언 > 코드실행 순으로 진행된다.

### 1. var

var로 선언한경우 hoisitng되는 동시에 초기화가 진행된다. 따라서 hoisitng은 되었지만, console.log로 확인해봤을때 undefined가 출력이 된다.

### 2. let, const

let과 const로 선언하는 경우 hoisitng은 되지만 ReferenceError가 나온다.

## TDZ (Temporal Death Zone)

임시적으로 죽어있는 공간. 선언 전에 변수를 사용하는 것을 비허용하는 이 개념상의 공간에 const와 let은 들어간다. 여기서 변수 선언과 할당 초기화 개념의 차이점에 대해 알 필요가 있는데, hoisitng이 되는 것은 변수의 선언만이다. var를 포함한 let, const 모든 선언은 hoisting이 일어난다. 즉 할당전에 console로 출력을 하게 되면 ReferenceError가 나온다. 이는 const와 let 선언이 hoisitng 되어 TDZ에 들어갔음을 의미한다.

## hoisintg과 var let const 개념 정리

var let const 의 선언은 hoisitng된다. var의 경우 TDZ에 들어가지 않고 선언 부분만 끌어올려졌기 때문에(hoisting) 할당되기 전까지 undefiend가 출력된다. (hositing과 동시에 초기화 할당한다고 생각할 수도 있다.) 하지만, let const의 경우 hoisting되며 일시적으로 죽어있는 공간(TDZ)에 들어가있기에 할당 전에 접근하려고 할 경우, ReferenceError 로 해당 변수에 참조할 수 없다는 에러가 출력된다.
