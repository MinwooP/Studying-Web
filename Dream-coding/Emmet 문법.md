# Emmet 문법

> `+ tab` 은 생략하겠음 !

html 양식 작성 => ! 

<br>

div 태그 작성 => div 

div에 id를 할당 => div#id_name 

div에 class할당 => div.class_name

사실 div는 가장 기본적인 tag이기 때문에 

.class_name 만해도 => div 태그가 만들어진다. 

<br>

**부모, 자식, 형제 노드**

div>ul>li

=> 

```html
<div>
    <ul>
        <li></li>
    </ul>
</div>
```

<br>

div>ul+ol

=> 

```html
<div>
    <ul></ul>
    <ol></ol>
</div>
```

<br>

ul>li*5

```html
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```

<br>

<!-- ^ -->  꺾새 활용

div>ul>li^ol

=> div 안에 ul를 만들고 그 안에 li를 만들었는데, 생각해보니 ul의 형제로 ol을 넣고 싶음. 그럴 때 `^` 를 사용하면 부모 태그에 형제 태그를 추가할 수 있음

```html
<div>
    <ul>
        <li></li>
    </ul>
    <ol></ol>
</div>
```

<br>



**그룹화하기**

```html
<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```

이 태그를 emmet 단축기로 만들려면

=> div>(header>ul>li*2>a)+footer>p



**텍스트 입력하기**

p{hello}

=> `<p>hello</p>`



**자동 번호 넣기**

p.class${item $}*5

=> 

```html
<p class="class1">item 1</p>
<p class="class2">item 2</p>
<p class="class3">item 3</p>
<p class="class4">item 4</p>
<p class="class5">item 5</p>
```



**더미용 텍스트 생성**

p>lorem

=> 

```html
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Architecto dolore repellat ab accusamus amet aliquam nihil earum ipsa, eius inventore ipsum maiores alias unde harum cumque officia magnam praesentium. Facere.</p>
```



p>lorem4

=> 4개의 단어만 생성해줘 !

`<p>Lorem ipsum dolor sit.</p>`

