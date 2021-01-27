---
layout : post
title : JavaScript
color: rgb(242,85,44)
tags: [websolute,team,JavaScript,web,front-end,back-end]
---

## What is JavaScript?
- 프로토타입기반의 프로그래밍 언어로, 스크립트 언어에 해당된다. 특수한 목적이 아닌 이상 모든 웹 브라우저에 인터프리터가 내장되어 있다. 오늘날 HTML, CSS와 함께 웹을 구성하는 요소 중 하나다. HTML이 웹 페이지의 기본 구조를 담당하고, CSS가 디자인을 담당한다면 JavaScript는 클라이언트 단에서 웹 페이지가 동작하는 것을 담당한다. 웹 페이지를 자동차에 비유하자면, HTML은 자동차의 뼈대, CSS는 자동차의 외관, JavaScript는 자동차의 동력이라고 볼 수 있다.
<br>
<br>

### script Tag
- ```<script></script>```를 통해 자바스크립트가 실행이 된다는 것을 알려줘야 한다.
~~~
<h1>JavaScript</h1>
<script>
  document.write(1+1);
</script>
<h1>html</h1>
1+1
~~~
위와 같이 코드를 실행 시켰을 때 자바스크립트는 동적이라 2라는 결과값이 나오고 HTML은 정적이라 1+1 이라고 나온다.
<br>
<br>

### 이벤트
- onclick, onchange, onkeydown 은 event로 사용자와 상호작용하는 코드를 만드는 것이 가능하다.
~~~
<input type="button" value="hi" onclick="alert('hi')">
<input type="text" onchange="alert('changed')">
<input type="text" onkeydown="alert('key down!')">
~~~

```<input type = "button" value = "hi" onclick = "alert('hi')">```
hi라는 버튼을 만들고 클릭했을 때, hi 표시
```<input type = "text" onchange = "alert('changed')">```
박스 안에 text를 입력받으면 changed 표시
```<input type = "text" onkeydown = "alert('key down!')">```
사용자가 키보드키를 눌렀을 때, key down!를 표시
<br>
<br>

### 콘솔창
- 자바스크립트 파일을 통해서가 아닌 콘솔창을 띄워서도 사용가능! 
마우스 우클릭을 하여 검사버튼을 누르고 콘솔창을 띄워 여러 행동을 할수 있다.
<br>
<br>

### var와 const
~~~
var a = 'test'
var a = 'test2'
// 이미 만들어진 변수이름으로 재선언했는데 아무런 문제가 발생하지 않는다.
const b = 'test'
const b = 'test2'
// 오류
~~~
const는 var와 다르게 중복선언이 불가능하다, 또한 재할당이 가능(var)하고 불가능(const)한차이가 있다.
둘다 변수 선언할때 쓴다!
<br>
<br>

### 제어할 태그 선택
~~~
<h1><a href="index.html">WEB</a></h1>
  <input type="button" value="night" onclick="
    document.querySelector('body').style.backgroundColor = 'black';
    document.querySelector('body').style.color = 'white';
  ">
  <input type="button" value="day" onclick="
    document.querySelector('body').style.backgroundColor = 'white';
    document.querySelector('body').style.color = 'black';
  ">
  <ol>
    <li><a href="1.html">HTML</a></li>
    <li><a href="2.html">CSS</a></li>
    <li><a href="3.html">JavaScript</a></li>
  </ol>
  <h2>JavaScript</h2>
  ~~~

  ```<input type="button" value="night" onclick=``` night라는 이름의 버튼을 생성
  ```document.querySelector('body').style.backgroundColor = 'black';```
  ```document.querySelector('body').style.color = 'white';```body의 뒷배경색을 검은색으로, 글자색을 흰색으로 만든다.
  <br>
  <br>

### 객체
- 객체의 사용법 : 읽고 쓰기 방법
~~~
var coworkers = {
  "programmer" : "A",
  "designer" : "B"
};
document.write("programmer : " + coworkers.programmer + "<br>");
document.write("designer : " + coworkers.designer + "<br>");
coworkers.bookkeeper = "duru";
document.write("bookkeeper : " + coworkers.bookkeeper + "<br>");
coworkers["data scientist"] = "C";
document.write("data scientist : " + coworkers["data scientist"] + "<br>");
~~~
<br>

- 객체의 사용법 : 반복문을 이용한 모든 정보 가져오기
~~~
for (var key in cowerkers){
  document.write(key + ' : ' + cowerkers[key] + '<br>');
}

//출력값
programmer : A
designer : B
bookkeeper : C
data scientist : D
~~~
<br>

- 객체의 사용법 : 객체프로퍼티와 메소드
~~~
cowerkers.showAll = function(){
  for(var key in this){
    document.write(key + ' : ' + this[key] + '<br>');
  }
}

// 출력값
programmer : A
designer : B
bookkeeper : C
data scientist : D
showAll : function(){for(var key in this){document.write(key + ' : ' + this[key] + '<br>');}}
~~~
<br>
<br>

### 파일 분할을 이용한 정리정돈

```<script src = "JS_name.js"></script>```을 이용하여 Javascript 파일을 다른 파일로 저장한 후에 HTML 파일에서 사용가능
<br>
<br>

### 라이브러리와 프레임워크
- 라이브러리 : 활용가능한 도구들의 집합
- 프레임워크 : 소프트웨어의 특정 문제를 해결하기 위해서 상호 협력하는 클래스와 인터페이스의 집합

<p align="center"><img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcxhwUO%2FbtqDiE7jcdg%2FgvcYbBkP9mGtmTWAMgIhq0%2Fimg.png" width="75%"></p>
