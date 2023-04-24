# CSS

## 🚩CSS란?

Cascading Style Sheet

Cascading => 작은 폭포, 위에서 아래로 떨어지는, 연속된 이라는 뜻이다. 

개발자가 정의한 스타일링 문서가 있고, 스타일링을 작성하지 않아도 브라우저 상에서 기본적으로 보여지게 만들어주는 기본 style sheet 이 있다. 

=> 브라우저 상에 버튼을 만들었다면, 우선 직접 정의한 style sheet에서 그 버튼에 대한 styling이 있는지 확인하고, 없다면 기본 style sheet에서 찾는다.

=> 이처럼 Cascading은 정의된 세부적인 스타일이 있다면 그것을 쓰고, 없다면 다음 기본으로 지정된 스타일로 넘어감을 의미. 

<br>

웹사이트를 styling할 때, 크게 3가지로 나눠볼 수 있음

1. Author style

   + 내가 작성하는 css 파일

2. User style

   + 사용자가 설정하는 styling

     => 브라우저 상에서 사용자가 dark mode를 쓸 건지, 글자 크기를 조정하고 싶은 지 등 브라우저에서 스타일링을 바꿀 수 있는 것 

3. Browser

   + 브라우저 상에서 기본으로 지정된 style

=> Cascading은 1=>2=>3 순서로 진행됨. 

> ` ! important`를 통해 이 cascading을 끊을 수있음

<br><br>

## 🚩 Selector

기본 format

```css
selector {
    property: value;
}
```

![image-20230206174400365](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230206174400365.png)

<br>

Universal => `*`

```css
* {
   color : green;
}
```

+ 모든 태그들을 선택
+ 모든 태그들의 color가 green으로 설정 됨

<br>

type => `Tag`

```css
li {
  color: blue;
}
```

+ 특정 태그를 선택할 수 있음

<br>

Id => `#id`

```css
#special {
  color: pink;
}
```

<br>

Class => `.class`

```css
.red {
  width: 100px;
  height: 100px;
  background: yellow;
}
```

<br>

State => `:`

```css
button:hover {
  color: red;
  background: beige;
}
```

+ 같은 버튼이라도 버튼 위에 마우스를 올렸을 때 특정한 효과를 줄 수 있음

<br>

Attribute => `[]`

```css
a[href]{
    color: purple;
}
```

+ `<a>` 태그 중, `href` 속성 값이 있는 태그들만 특정한 효과를 줄 수 있음.

<br><br>

## 🚩Styling

padding => content 안에 들어있는 spacing

margin => content 밖에 들어가는 spacing

<br><br>

## 🚩display와 position

웹 사이트를 만들 때 가장 중요한 것은 ? 

=> 우리가 만들려는 box들을 원하는 위치에, 원하는 크기로 배치할 수 있는 것.

=> 이를 위해서는 **display**와 **position**을 잘 알아야 함.	

<br>

### display

`<div> ` => block level

`<span>` => inline level

![image-20230206230850687](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230206230850687.png)

이렇게 `div`는 기본적으로 block level (`display: block;`)이라서 한 줄에 하나씩 나오고, `span`은 기본적으로 inline-level (`display: inline;`) 이기 때문에 한 줄에 공간이 충분하면 여러 개가 동시에 나옴.

> 그럼 span 태그는 inline 요소이므로 width, height을 80px로 설정해도 이게 적용이 되지 않음 ?

=> 하지만 이 기본값은 CSS를 통해 변경이 가능함.

```css
span {
    display: block;
}
```

=> 이렇게 `span`의 display 속성을 `block`으로 바꿔주면 `div` 처럼 한줄에 하나씩 `span` element들이 배치되는 것을 볼 수 있음.

마찬 가지로 `div`의 display 속성을  `inline-block`으로 바꿔주면 기존 `span` element처럼 한줄에 여러 개의 element가 배치되는 것을 볼 수 있음.

그런데 여기서 display 속성을 `inline-block`이 아닌, `inline`을 준다면

```css
div {
    display: inline;
}
```

=> 현재 `div` 안에 아무런 내용이 없어서 브라우저에 아무것도 표시되지 않음

=> 하지만 `<div> 1 </div>` 이렇게 안에 내용을 넣으면, `span` 태그와 마찬가지로 `inline`이 되어서 보여진다. `inline` 이라는 것은 내용 자체만을 꾸며주는 것. 

=> `inline`이란, 우리가 css에서 width나 height을 정의한 것은 무시하고, content의 크기에 맞추어서 element의 크기가 변경되는 것.

vs `inline-block`은 `inline`처럼 한 줄에 여러 개의 element들을 위치시키지만, block 단위로 변환되어서 태그 안의 content의 크기와는 상관없이 우리가 지정한 box의 `width`와 `height`에 맞추어서 크기가 정해지는 것.  

정리하면, 

=> 

`inline` : content의 크기에 따라 한 줄로

`inline-block` : box의 크기에 따라 한 줄로

`block` : 한 줄당 하나씩 들어가는 box

> ```css
> div, span {
>     width: 40px;
>     height: 40px;
> }
> ```
>
> 이렇게 css 파일에 정의된 `div`나 `span` 태그의 `width`나 `height` 속성의 값은 content의 크기를 의미하는 것이 아니라 `div`나 `span`이 정의하는 ***element 전체의 크기***를 의미한다. 

<br>

### position

css에서 지정된 `position` 의 기본 value는 `static`이다.

1. **static**

   => html에 정의된 순서대로 브라우저 상에 자연스럽게 보여줌. 

2. **relative**  

   => **원래 있어야 하는 자리**에서 상대적으로 옮겨가도록 

   => 설정된 left와 top 등의 값에 따라 위치가 결정됨.  

   > 원래 있어야 하는 자리 : 원래 기존 position의 value가 static 이었을 때 element가 있어야 하는 자리 => html에 정의된 순서대로 배치되어 있어야 하는 자리

3. **absolute** 

   => 해당 element의 ***바로 위 parent Box tag를 기준으로*** 삼아서 위치를 설정함. 

   EX)

   ```html
   <body>
       <article class="container">
       	<div></div>
           <div class="box">I'm box</div>
           <div></div>
           <div></div>
           <div></div>
           <div></div>
           <div></div>
           <div></div>
           <div></div>
           <div></div>
   </body>
   ```

   ```css
   .container{
       
   }
   
   .box{
       left: 20px;
       top: 20px;
       position: absolute;
   }
   ```

   => 여기서 `box`의 position은 `box`의 상위 box 태그인 `container`를 기준으로 왼쪽에서 20px, 위에서 20px 만큼 떨어지도록 위치가 설정 됨.  

4. **fixed**

   => 해당 element가 담긴 상자(상위 box 태그) 안에서 완전히 벗어나서, window 안에서 움직이는 것

   => 상위 box 태그들을 다 무시하고, **해당 페이지 안에서 위치를 설정**함.  

5. **sticky**

   => 원래 있어야 하는 자리에 있으면서(static 상태에서) 스크롤 되어도 없어지지 않고 원래 있던 자리에 그대로 붙어있도록 설정 

<br>

## 🚩CSS의 꽃 : Flex box

Flex box => box와 item들을 행 또는 열로 자유자재로 배치시켜줄 수 있는 유연한 기능

<br>

아주 예전에는 모든 브라우저에서 호환가능하면서 강력하게 레이아웃을 만들기 위해

position이나 float, table을 이용해서 layout을 구성했음.

=> 하지만 이들만으로는 불가능한 작업도 존재했음

<br>

### float

![image-20230207004325495](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230207004325495.png)

+ float의 원래 목적은 image와 text를 어떻게 배치할 것인지를 정의하는 것 

+ `float: left` 라고 지정하게 되면, image가 왼쪽에 배치되고, text들이 이 이미지를 감싸면서 배치될 수 있도록 해줌.

  예전에는 이렇게 css의 layout을 지정할 수 있는 기능이 없다보니까 많은 사람들이 float을 이용해서 box를 왼쪽에, 오른쪽에 배치하고 그랬음 

  => 하지만 이는 float의 원래 목적에 어긋난 일종의 Hack

  => 하지만 현재 flex-box의 등장으로 float은 원래 목적으로만 쓰이게 됨.

<br>

### Flex-box

Flex-box의 2가지 특징 

1. container, 즉 box에 적용되는 속성 값들이 존재하고, 각각의 item들에게 적용될 수 있는 속성 값도 존재한다. 

+ **container**에게 적용되는 속성 값들
  
  + `display`  : flex 로 설정하면, 해당 컨테이너는 flex-box로 지정
  
  + `flex-direction` => 중심축을 어떤 방향으로 할지 => 기본값:  row
  
    => 아이템을 세로로 정렬하고 싶으면 `column`으로 설정하면 됨. 
  
  + `flex-wrap`
  
     `flex-wrap: wrap`으로 바꾸게 되면 item들이 한 줄에 꽉 차게 되면 자동으로 다음 줄로 item들이 넘어감 
  
  + `flex-flow` => direction과 wrap을 한번에 쓸 수 있음 => 중요x
  
  + `justify-content `=> 중심축을 아이템들을 어떻게 배치할지
  
    flex-direction이 row이면, 우선 아이템들을 가로로 정렬할 건데
  
    + flex-start: 기본값으로, 왼쪽 => 오른쪽으로 배치 
    + center : 가운데로 모아줌.
  
  + `align-items`=>중심축을 기준으로 아이템을 어떻게 배치할지
  
    
  
  + `align-content`
  
+ **item**에게 적용되는 속성 값들

  + `order`

  + `flex-grow`

    `1`로 설정한다면, container가 커질 때, 아이템들도 커져서 container를 꽉 채움 

    `0` => container가 커져도 item들은커지지 않음

  + `flex-shrink`

    `1` => container가 작아지면, item도 같이 작아짐

    `0 `=> container가 작아지면, item은 작아지지 않음 

  + `flex`

  + `align-self`

=>  flexbox의 전체적인 정렬과 흐름 속성은 부모인 flex container에서 정의하고, 크기나 순서에 관련된 속성은 자식 요소에 해당하는 flex-item에서 정의합니다.

<br>

2. flex-box에는 중심축과 반대축(중심축에 수직을 이루는 축)이 있다.

   => 중심축을 수평에 두는지 수직에 두는지에 따라서 반대축이 바뀐다. 

   <br>

demo를 통해 알아보자

```html
<body>
    <div class="container">
        <div class="item item1">1</div>
        <div class="item item2">2</div>
        <div class="item item3">3</div>
        <div class="item item4">4</div>
        <div class="item item5">5</div>
        <div class="item item6">6</div>
        <div class="item item7">7</div>
        <div class="item item8">8</div>
        <div class="item item9">9</div>
        <div class="item item10">10</div>
	</div>
</body>
```

```css
.container {
    background: beige;
    height: 100% or 100vh ;
}

.item{
    width: 40px;
    height: 40px;
}

```

+ `height: 100%` 

  해당 element가 들어있는 **부모의 높이에 100%로 채우겠다**는 의미

  => 현재 `container`의 부모는 `<body>` 이므로, `<body>`의 높이에 100%로 채우겠다는 뜻

+ `height: 100vh`

  부모에 상관없이 item을 보이는 view port의 height의 100%를 다 쓰겠다. 

<br>

#### container 속성 값들

`display: flex`

flex-box를 만들기 위해선,

우선 container level의 box에게 "너 이제부터 flex-box야 !" 라고 말해줘야 함.

`display: flex;` 속성을 추가해주면 됨.

```css
.container {
    background: beige;
    height: 100vh;
    display: flex;
}
```

=> 그러면 item들이 자동으로 *왼쪽 =>오른쪽* 으로 정렬 됨.

=> 이는 `flex-direction`의 default 값이 `row` 여서 그런 것.

=> 여기서 중심축은 row = x축 = 수평축이 되는 것.

 <br>

`flex-direction`

=> 중심축이 어디인지를 가르쳐주는 속성

=> `flex-direction`의 default 값은 `row`  

=> `flex-direction: row-reverse;`로 변경하면, *오른쪽 => 왼쪽* 으로 정렬이 바뀜

=> item들이 오른쪽 끝에서부터 정렬이 시작됨. 즉 화면의 오른쪽으로 붙음.

> 여기서는, 오른쪽 끝에서부터 처음 item부터 정렬이 시작되는 것이기 때문에 정렬 순서 자체가 뒤집어지면서, 아이템들의 배치 위치도 달라지는 것이고 뒤에서 나올 `justify-content: flex-end` 속성 값의 효과는 정렬은 처음 item부터 그대로 되는 것이지만, item들의 위치만 오른쪽으로 붙는 것이다.  

=> 여전히 중심축은 row

=> 중심축을 바꾸고 싶다면 `flex-direction`을 `column` 혹은 `column-reverse`를 설정해주면 됨

=> 중심축은 `column` = y축 = 수직축이 됨.

 <br>

`flex-wrap `

flex-box 안에 만약 item들이 더 많이 있다면, item들이 자동적으로 한 줄에 빼곡하게 붙어있음

=> wrapping을 안하겠다라고 기본값으로 `flex-wrap: nowrap`으로 지정되있기 때문.

=> `flex-wrap: wrap`으로 바꾸게 되면 item들이 한 줄에 꽉 차게 되면 자동으로 다음 줄로 item들이 넘어감 

=> `flex-wrap: wrap-reverse`로 바꾸게 되면 아래=>위로 wrapping 되도록 바꿀 수 있음.

 <br>

`flex-flow`

이는 `flex-direction`과 `flex-wrap `을 한꺼번에 쓰기 위한 것이다.

```css
.container {
    background: beige;
    height: 100vh;
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
}

== 

.container {
    background: beige;
    height: 100vh;
    display: flex;
    flex-flow: column nowrap;
}
```

 <br>

아이템들을 어떻게 배치할 것인지를 알아보자. 

 <br>

`justify-content` 

=> ***중심축을 기준으로*** 아이템들을 어떻게 배치할지를 결정하는 것.

+ `justify-content: flex-start;` => 기본값 ?

  => 수평축이 중심축이라면 왼쪽=>오른쪽으로 item들 배치

  => 수직축이 중심축이라면 위쪽=>아래쪽으로 item들 배치

+ `justify-content: flex-end;`

  => ***item들의 정렬 순서(왼쪽 => 오른쪽)은 유지하되***  item들을 오른쪽=>왼쪽으로 배치

  > 위에서 설명한 

+ `justify-content: center;`

  => 아이템들을 center에 모아줌

+ `justify-content: space-around;`

  => box를 둘러싸도록 spacing을 넣어줌.

  => 양옆이 제일 크기가 작은 spacing이 들어감.

+ `justify-content: space-evenly;`

  => spacing을 양 옆 중간 모두 같은 크기로 넣어줌
  
+ `justify-content: space-between;`

  => 아이템들을 양 끝에 배치해줌.

 <br>

`align-items`

=> ***반대축을 기준으로*** 아이템들을 어떻게 배치할지를 결정하는 것.

+ `align-items: stretch` (기본값)

  => 아이템들이 수직축 방향으로 끝까지 쭈욱 늘어납니다.

+ `align-items: center;`

  => 반대축의 중심에 item들을 배치 

+ `align-items: baseline;`

  => 아이템들을 텍스트 베이스라인 기준으로 정렬합니다.

 <br>

`align-content`

=> `flex-warp : wrap;`이 설정된 상태에서, 아이템들의 행이 2줄 이상 되었을 때의 수직축 방향 정렬을 결정하는 속성이다. 

`justify-content` 는 중심축을 기준으로 아이템들을 배치한다면, `align-content;`는 반대축을 기준으로 아이템들을 배치한다.

 <br>

#### item 속성 값들

```css
.item{
    width: 40px;
    height: 40px;
    border: 1px solid black;
}

.item1{
    background: ~;
    order: 0;
}
```

 <br>

`order`

=> item의 우선순위를 나타냄

=> 현업에서는 잘 쓰지 않음

 <br>

`flex-grow`

=> 이를 쓰지 않으면 item들은 원래 사이즈 40, 40씩을 유지하고 있음. container가 아무리 커져도 40, 40을 유지하다가 container가 너무 작아지면 어쩔 수 없이 한 줄에 꽉 차있어야 하니까, item들이 작아짐

=> 하지만 `flex-grow: 1;`로 변경한다면, container를 꽉 채우려고 item들이 늘어나게 됨.

=> 각 item들의 `flex-grow`의 숫자를 서로 적절히 조정함으로써, 늘어나는 비율을 맞출 수 있음

 <br>

`flex-shrink`

=> 위와 반대로 container가 점점 작아졌을 때, item들이 얼마나 줄어드는지를 나타냄

=> 값이 클수록, 더 많이 줄어듬.

 <br>

`flex-basis`

=> flex item의 기본 크기를 결정하는 속성

=> item들이 공간을 얼마나 차지해야 하는지

=> flex-basis 속성의 값을 auto로 설정하면 flex item은 상대적 flex item(relative flex item)이 되어 콘텐츠의 크기를 기준으로 크기가 결정됩니다.

 <br>

![image-20230411195942515](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230411195942515.png)

​	

item별로 각 item들을 정렬 가능

=> 특정한 item만 다르게 정렬할 때 사용





+ flex box 게임 : https://flexboxfroggy.com/#ko

+ CSS flex 정리 

  https://studiomeal.com/archives/197

  https://narup.tistory.com/210

  