# data attributes

html 태그 자체에서 제공하는 속성들 뿐 아니라 내가 원하는 data를 html 태그, 즉 돔 요소에 추가할 수 있도록 해줌.

<br><br>

`data-*`

```html
<body>
    <div data-index="1" data-display-name="dream"></div>
	<div data-index="2" data-display-name="coding"></div>
</body>
```

html에서 기본으로 제공하는 속성은 아니지만, 원하는 data를 넣은 data attributes를 이용할 수 있음

<br><br>

css에서도 이러한 data attribute를 꾸며줄 수 있음

=> CSS 선택자

```html
<style>
div[data-display-name='dream']{
          bac
</style>
```

<br><br>

js에서 이러한 data attribute가 추가 된 html 태그를 선택하는 방법

```html
<script>
	const dream = document.querySelector('div[data-display-name="dream"]');
</script>
```

<br>

```html
<script>
	const dream = document.querySelector('div[data-display-name="dream"]');
    console.log(dream.dataset);
    console.log(dream.dataset.displayName);
    console.log(dream.dataset.index);
</script>
```

<br>

`console.log(dream.dataset);`

=> 

DOMStringMap

displayName: "dream"

index: "1"

=> dataset에 접근하면 이렇게 `data-` 앞부분은 없어지고 뒷부분은 `-`를 기준으로 camelCase화 되어서 나옴.

<br>

=> 돔 요소에 이렇게 추가하는 data들은 사용자들이 html 파일을 다운 받으면 이 data들이 다 보인다.

=> 그래서 중요하거나 민감한 data들은 돔 요소가 아닌 js 안에 보관하는 것이 보안상 안전하다.