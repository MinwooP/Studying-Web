# HTML BASIC

이미지 파일을 열면 컴퓨터에 기본으로 지정된 이미지 뷰어가 실행되면서 이미지 내용이 보여지고

음악 파일을 열면 음악 재생 프로그램이 실행되듯이

=> **html** 파일을 열면, 컴퓨터에 기본으로 지정된 **크롬 브라우저**가 실행되면서 HTML의 내용이 표시됨

<br>

#### 🚩html

+ 웹을 이루는 기본 구조

+ 웹 컨텐츠의 구조와 의미를 결정

+ css와 js는 부가적인 요소일 뿐

+ HTML은 웹 브라우저 상에서 보여지도록 디자인 된 문서로, 표준화된 mark up 언어를 사용하고 있음

  > mark-up 언어 : 일반적인 텍스트와 구분하기 위해 문서에 annotating 된 것 



```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>

</body>
</html>
```

`<!DOCTYPE html>`

=> *document type이 html이다*  라고 정의하는 것. 

=> html 문서의 버전을 웹 브라우저에게 알리는 것. 이를 선언하지 않으면 같은 내용의 HTML 문서라도 각 브라우저의 환경에 따라 전혀 다른 결과물을 출력하는 경우가 발생. 따라서 각 브라우저가 HTML 문서를 동일하게 인식할 수 있도록하기 위해 선언. 

=> HTML5 이전에는 DOCTYPE을 선언하는 코드가 길었지만, 현재 HTML5 등장으로 이를 웹 표준으로 정착해서 사용하고 있음.  

> https://ssd0908.tistory.com/entry/HTML-DOCTYPE-%EC%84%A0%EC%96%B8-%EC%9D%98%EB%AF%B8-%EB%B0%8F-%ED%98%84%EC%9E%AC%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94%EA%B0%80



`<html>`

html 파일 제일 상위에 있는 태그



`<head>`

+ 사용자에게 보여지는 UI적인 요소가 전혀 포함되어 있지 X
+ 구글에서 검색할 때 나오는 파일들이나 부가설명, 북마크 추가할 때 나오는 제목이나 아이콘 등이 정의되어있음
+ CSS 파일을 연결하는 것도 이 부분에서 진행
+ 사용자에게 보여지는 정보는 없고 **meta-data** 만 있다



` <meta charset="utf-8">`

+ 이 페이지에서 쓰여지는 character의 format은 utf-8을 쓴다는 뜻

+ utf-8은 현존하는 모든 사람들이 쓰는 언어를 지원해주기 때문에 기본으로 이걸 사용하면 됨.



`<body>`

+ 사용자에게 보여지는 요소 중 최상위 container

+ `<body>` 안에 `<h1>`, `<h2>`, `<button>` 태그를 텍스트로 쓰면 브라우저 상에서는 제목과 버튼이 보여질 수 있는 이유

  => 모든 브라우저들이 W3C 라는 표준을 따르도록 구현되어있기 때문에 

 

>  **W3C** 
>
> world wide web consortium
>
> + 웹의 표준화를 추진하는 곳
>
> + 예를 들어 W3C에서 "html5에는 이러이러한 태그가 있어 ~" 라고 정의를 하면 세상에 존재하는 모든 브라우저들이 이 표준에 맞게 브라우저를 구현해야 함.
>
>   => 그래서 우리가 html에 정의된 태그를 사용해서 페이지를 디자인할 때, 모든 브라우저 상에서 잘 이러한 태그들이 잘 표현될 거라고 믿고 하는 것.



> html 태그 오류 검사 사이트
> https://validator.w3.org/#validate_by_input