# HTML 태그

상자를 많이 세분화해서 만드는 게 중요

박스 모델을 이용한 태그 정리

<br>

![image-20230206233150976](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230206233150976.png)

모든 태그는 크게 2가지 종류로 나눠지고, ITEM 태그는 또 2개 LEVEL로 나눌 수 있음. 

1. BOX => SECTIONING을 도와주는 BOX 태그
2. ITEM => 브라우저 위에서 실제로 보여지는 ITEM 태그
   + Block => 1줄에 하나
   + Inline => 공간이 허용하면 다른 태그 옆에 배치 가능 

<br><br>

#### 🚩Box 태그

`<header></header>`

`<footer></footer>`

`<section></section>`

`<div></div>`

`<span></span>`

<br><br>

#### 🚩Item 태그

`<button></button>`

`<a></a>`

<br><br>

`<a>` 태그

=> 링크를 걸어주는 태그

```html
<a href = "https://google.com" target = _blank>Click</a>
```

<br>

`<p>` 태그

=> 문단을 구분할 때 사용

```html
<p>This is a sentence. <b>That</b> is..</p>
<p>This is a sentence. <span>That</span> is..</p>
<p>This is a sentence. <div>That</div> is..</p>
```

`<b>` => inline level => element를 bold 체로 강조해줌

`<span>` => inline level => span 태그로 감싸진 element가 다음 줄로 넘어가지 않음 

`<div>` => block level => div 태그로 감싸진 element는 다음 줄로 넘어감

=> inline, block level의 어떤 태그를 사용하느냐에 따라서 자동으로 줄바꿈이 일어나는지 여부가 결정됨.

<br>

List 태그 => `ol`, `ul`, `li`

ol 태그 => 순서가 있는 list 

```html
<ol>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ol>


ol>li*3 을 type하고 tab을 누르면 위의 코드가 자동 생성 됨 ! 
```

<br>

ul 태그 => 순서가 없는 list

```html
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>
```

<br>

<br>

input 태그 => 사용자에게 입력을 받는 태그

```html
<label for="">Name: </label>
<input id="input__name" type="text">
```

+ 브라우저에서 굉장히 흔하게 쓰이는 태그 

  => 사용자에게 원하는 데이터를 입력받을 수 있기 때문

  => 보통 `<label>`태그와 같이 사용됨(사용자에게 어떤 정보를 원하는지 명확하게 나타내주기 때문)

+ label이나 input 태그 모두 inline element이므로, 둘다 한줄에 동시에 표시됨
+ 그리고 한 페이지 안에 여러개의 input이 필요할 수 있기 때문에, input 태그에 고유한 식별자인 id를 부여해줌. 

+ 속성 중 `type`을 `text`, `checkbox`, `button`, `file` 등으로 변경함으로써 원하는 입력의 형태에 따라서 원하는 input 태그의 type을 설정할 수 있다. 
