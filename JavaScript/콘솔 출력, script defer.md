## 🚩콘솔에 출력해보기

**Hello world !** 출력해보기

바탕화면의 프로젝트 폴더에 `main.js` 파일을 만들고

```javascript
console.log('Hello world!');
```

를 적고, 저장한 후

<br>

window shell 에서 프로젝트 폴더로 이동한 후, 

`> node main.js`를 실행하면

=>  `Hello world !`가 출력되는 것을 확인할 수 있다.

=> ***이는 윈도우에 node js가 설치되어있기 때문에 가능한 것***

=> node js에는 javascript engine이 있어서 브라우저 없이도 js를 실행할 수 있음

<br>

이렇게 node js를 이용해서도 콘솔창에 출력할 수 있고, web API를 통해서도 할 수 있다.

<br><br>

-----

## 🚩script async vs defer

HTML에서 Js를 포함할 때, 어떻게 포함하는 게 더 효율적인지

<br>

##### 1. `<head>` 안에 `<script>`를 포함했을 때

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src = "main.js"></script>
</head>
<body>

</body>
</html>
```

사용자가 html 파일을 다운로드 받았을 때

=> parsing HTML (브라우저가 html 파일을 한줄한줄 분석)

=> 이렇게 분석한 것을 css와 병합해서 dom 요소로 변환

=> 이렇게 한줄 한줄 분석하다가 `<script>` 태그가 보이면,  *`main.js` 를 다운 받아야 하네 ?* 라고 생각

=> html 파싱을 멈추고, 필요한 js 파일을 서버에서 다운받아서 이를 실행한 다음에 다시 parsing 



이러한 방식의 단점 ?

=> 나의 js file의 크기가 엄청크고, 인터넷 속도도 엄청 느리다면 사용자가 나의 웹사이트를 보는데까지 많은 시간이 소요

=> `<script>`를 `<head>`에 포함하는 것은 좋지 X



##### 2.  `<body>` 마지막에 `<script>`  포함

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
	<div></div>
    <script src = "main.js"></script>
</body>
</html>
```

브라우저가 html 파일 쭉 파싱해서 페이지가 준비된 다음

=> `<script>` 를 만나서, js file을 서버에서 받아오고 실행

=> js file을 받기전에도, 페이지 컨텐츠가 준비가 되서 사용자에게 보여짐

<br>

이러한 방식의 단점?

=> 사용자가 기본적인 html의 컨텐츠를 빨리 볼 수 있지만, 사용자가 정상적인 페이지를 보기전까지 많이 기다려야 된다.



##### 3. `<head>` + async 

`<head>`안에 `<script>`를 넣되, **async**라는 속성값 주기

**`<script asyn src = "main.js"></script>`**

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script asyn src = "main.js"></script>
</head>
<body>

</body>
</html>
```

+ **asyn**는 boolean type의 속성 값이기 때문에 선언하는 것만으로도 **true**로 설정된다. 

<br>

async를 사용하게 되면, 브라우저가 html을 파싱하다가

=> `<script>` 를 만나면 병렬적으로 

1. `main.js` 파일을 다운로드 받으면서
2. html 파싱도 계속함

=> `main.js` 다운로드가 끝나면, 그때 parsing을 멈추고 다운로드 된 js 파일을 실행

=> js 실행 후, 나머지 html을 파싱

+ 이러한 방식의 장점

  => `<body>` 끝에서 사용하는 것보다는 html을 parsing 하는 동안 js fetching이 병렬적으로 이루어졌기 때문에  다운로드 받는 시간을 절약 가능, 

+ 단점

  하지만 html이 다 parsing 되기도 전에 js가 실행되기 때문에

  => 만약 js 파일에서 쿼리 셀렉터를 이용해서 dom 요소를 조작한다 그러면, 조작 시점에 html에 원하는 요소가 아직 정의되어 있지 않을 수 있어서 위험할 수 있음. 

  그리고 html을 parsing 하는 동안 언제든지 js를 실행하기 위해 멈출 수 있기 때문에, 사용자가 페이지를 보는데 시간이 여전히 걸릴 수 있음

<br>

##### 4. `<head>` + defer

#####  **`<script defer src = "main.js"></script>`**

asyn와 비슷하지만

`<script>`를 만났을 때

=> 병렬적으로 `main.js`를 다운로드 받으면서 `html` 파싱도 하지만,

=>`html` 파싱이 모두 끝난 후에 사용자에게 페이지를 보여준 다음에 ! 다운로드 된`main.js` 실행

<br>

=> defer 옵션을 쓰는 것이 가장 효율적이고, 안전함

> Q)
>
> 위의 4가지 상황을 다 봤을 때, HTML parsing과 js file download는 병렬적으로 할 수 있지만, HTML parsing과 js 실행은 동시에 못하는 것 같다. 왜 ?

<br>

## 🚩 use strict

```javascript
'use strict';

console.log('Hello world!');
```

이렇게 js를 이용할 때, 제일 위에 `use strict`를 선언해주면 좋음

=> 순수 바닐라 javascript 를 이용할 때는 쓰는 게 좋음



자바 스크립트는 굉장히 유연한 언어임

=> 개발자가 많은 실수를 할 수 있음

=> 때로는 아주 위험



EX) 

선언되지 않은 변수에 값을 할당,

기존에 존재하던 prototype을 변경한다던지

=> `use strict`를 ECMAScript에 추가되어 있으므로

이를 선언하게 되면 더 이상 위와 같은 비상식적인 것을 사용할 수 없게 됨



EX)

```javascript
console.log('Hello world!');

a = 6;
```

이렇게 `use strict`를 사용하지 않고 선언되지 않은 변수인 `a`에 값을 할당해서 실행하면, 브라우저에서는 전혀 문제가 될 게 없음

=> `use strict`를 선언하면 error가 뜸







## 🚩출처

https://www.youtube.com/watch?v=tJieVCgGzhs&list=PLv2d7VI9OotTVOL4QmPfvJWPJvkmv6h-2&index=2