# JavaScript

웹이 세상에 처음 등장했을 땐, HTML 밖에 없었다. HTML은 정적이다. 사용자와 상호작용하는 웹 페이지를 만들고 싶었다.

=>

그래서 태어난 기술이 **JavaScript** 

웹사이트들이 프로그램처럼 사용자와 상호작용하면서도 검색엔진을 통해서 검색된다는 것은 웹만이 가진 독창적인 특성



우리가 하고자 하는 것 => 사용자의 버튼 클릭에 따라 웹 페이지의 배경색 바꾸기 



onclick 속성의 값으로는 javascript가 와야한다. 

`document.querySelector(body)`

=> 현재 문서에서 `body` 태그를 선택 



-----

## 📌 script 태그

기본적으로 자바스크립트는 HTML 위에서 동작하는 언어.

HTML에 자바스크립트를 어떻게 낑겨넣을 것인가

```html
<script>
    script 태그 안에 자바 스크립트 코드를 작성
</script>
```



-----

## 📌 Event

자바스크립트가 사용자 상호작용 하는데 핵심적인 역할을 하는 것 

```html
<body>
        <input type="button" value = "hi" onclick="alert('hi')">
        <input type="text" onchange="alert('changed')">
        <input type="text" onkeydown="alert('key down!')">  
</body>
```

+ 웹 브라우저 위에서 일어나는 일들을 이벤트라고 한다. 어떤 이벤트가 일어났을 때, 어떠한 자바스크립트가 실행되도록 하는 것이 onClick, onchange,  onkeydown 같은 것. 

+ 일어날만한 이벤트

  + 클릭

  + 텍스트 입력 

    => 웹 브라우저는 웹 브라우저 위에서 일어나는 여러가지 이벤트 중, 중요한 10~20개 정도의 이벤트를 정의해놓고 있고, 우리는 이 이벤트들을 이용해서 사용자와 상호작용하는 웹 페이지를 만들 수 있다. 



-----

## 📌 콘솔

자바 스크립트를 실행하는 또다른 방법

우클릭 => 검사 => console 창 

console을 이용하면 html 파일을 만들지 않고도 자바스크립트 코드를 즉석에서 실행가능함.



콘솔에서 실행시키는 자바스크립트는 현재 보고있는 웹 페이지 안에 삽입되어있는 자바스크립트처럼 동작한다.

=> 현재 웹페이지를 대상으로 실행된다.



자바 스크립트를 이용한다는 것은 웹 페이지를 만드는 것처럼 거대한 목표일 수도 있지만, 

이미 만들어진 웹사이트를 나의 필요에 따라서 분석하고, 나의 문제를 해결할 수도 있다. 

ex) 페이스북 댓글 중 무작위 3명 추첨 



-----

## 📌 웹 브라우저 제어

지금부터는 자바스크립트를 통해서 할 수 있는 일 : 웹 브라우저 제어



css 기초

자바스크립트를 이용해 제어하고자 하는 태그를 선택하는 방법



-----

## 📌 css 기초

#### style 속성

+ `onclick` 속성 안에 자바스크립트가 오는 것과 마찬가지로 `style` 속성 안에는 css가 오는 것이 약속되어있음

+ 특정 태그를 css라는 언어로 디자인하고 싶을 때는 `style`이라는 속성을 쓰고, 그 안에 css의 속성이라는 문법을 사용하면된다. 

+ 글 중 특정 텍스트만 css로 꾸며주기 위해 아무 의미도 없이 태그로 묶어주고 싶을 때, `div` 태그나 `span` 태그 사용 가능

  => `div`는 줄바꿈 o, `span`은 줄바꿈 x

  ```html
  <span>JavaScript</span>kljflasfdas;ljf;askfdaskfaslfasfl;asfjaslfj;lasaf
  ```



#### style 태그

```html
<head>
        <style>
            .js{
                font-weight: bold;
            }
        </style>
</head>

<body>
        <h1><a href="index.html">WEB</a></h1>
        <h2 style="background-color:coral; color:powderblue">JavaScript</h2>
        <p>
            <span class = "js"> JavaScript </span> Lorem ipsum dolor, sit amet consectetur <span class = "js"> JavaScript </span> adipisicing elit. Consectetur fugiat cumque vel voluptas corporis necessitatibus quos fuga <span class = "js"> JavaScript </span>maiores architecto quod laborum quae tempora magniodio enim cum, facilis iste ducimus! <span class = "js"> JavaScript </span>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Incidunt sequi, nisi quas quis harum rem fugiat excepturi omnis quam molestiae <span class = "js"> JavaScript </span> repudiandae reprehenderit, aliquid esse noneveniet odit nam nulla expedita.
        </p>
</body>
```

+ `style` 속성을 각 텍스트에 다 적용하려면 `<span style="font-weight:bold;">JavaScript </span>` 이를 다 해줘야 하지만, `style` 태그를 사용해 각 텍스트에 class만 적용하면 쉬워진다. 





#### 선택자

`.`  => class를 의미

`#` => id를 의미 



+ `class`는 많은 요소들이 같은 클래스를 가지고 있지만, `id`는 특정 요소 하나에만 사용 가능

  => `class` 선택자보다 `id` 선택자가 더 우선 



```html
<head>
        <style>
            .js{
     			font-weight: bold;
      			color:red;
    		}
    		#first{
      			color:green;
    		}
    		span{
      			color:blue;
    		}
        </style>
</head>


<h1><a href="index.html">WEB</a></h1>
  <h2 style="background-color:coral;color:powderblue;">JavaScript</h2>
  <p>
    <span id="first" class="js">JavaScript</span> (/ˈdʒɑːvəˌskrɪpt/[6]), often abbreviated as JS, is a high-level, dynamic, weakly typed, prototype-based, multi-paradigm, and interpreted programming language. Alongside <span>HTML</span> and <span>CSS</span>, <span class="js">JavaScript</span> is one of the three core technologies of World Wide Web content production. It is used to make webpages interactive and provide online programs, including video games. The majority of websites employ it, and all modern web browsers support it without the need for plug-ins by means of a built-in <span class="js">JavaScript</span> engine. Each of the many <span class="js">JavaScript</span> engines represent a different implementation of <span class="js">JavaScript</span>, all based on the ECMAScript specification, with some engines not supporting the spec fully, and with many engines supporting additional features beyond ECMA.
  </p>
```



-----

## 📌 제어할 태그 선택하기

```html
 <body>
        <h1><a href="index.html">WEB</a></h1>
        <input type="button" value="night" onclick="
            document.querySelector('body').style.backgroundColor = 'black';
            document.querySelector('body').style.color = 'white';
            ">

        <input type="button" value="day" onclick="
            document.querySelector('body').style.backgroundColor = 'white';
            document.querySelector('body').style.color = 'black';
            ">
</body>ㅇ
```



자바스크립트라는 언어를 이론적으로 되돌아보자

자바스크립트는 컴퓨터 언어임에 동시에 컴퓨터 프로그래밍 언어

html은 컴퓨터 언어이지만 컴퓨터 프로그래밍 언어는 아님





순서에 따라서 실행되는 것을 Program 이라고 함.

따라서, Program이라는 말 안에는 순서라는 의미가 깊숙이 자리잡고 있음.

순서를 만드는 행위 => 프로그래밍

순서를 만드는 사람 => 프로그래머 



html은 웹페이지를 묘사하는 목적의 언어이기 때문에 시간의 순서에 따라 무엇을 할 필요가 없음

=> 정적이다. 

자바스크립트는 사용자와 상호작용하기위해 고안된 언어이고, 이를 위해서는 순서에 따라 실행되어야 함.  



