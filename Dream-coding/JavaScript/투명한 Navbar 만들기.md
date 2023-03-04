## 투명한 Navbar 만들기

> 맨 위에 달려있는 navbar를 투명한 navbar였다가, 스크롤 되었을 시 특정 색상의 배경을 띄고 페이지 상단에 고정되어있도록 구현해보자. 

<br>

우선, scrolling 되는 것을 알아야 함

=> navbar 높이 만큼 스크롤 되었을 때, navbar의 배경색을 변경할 것임

=> 그래서 우선 js code에서 현재 navbar의 height과 scroll된 위치를 알아야 함.

<br>

##### 1. scroll 된 위치

=> 구글에 ***javascript scroll position*** 검색

=> `var y = window.scrollY`를 통해 얼마나 스크롤이 되었는지 px 단위로 알려줌.

<br>

##### 2. navbar의 height 받아오기

=> 구글에 ***javascript element size*** 검색

=> `HTMLElement.offsetWidth`와 `HTMLElement.offsetHeight`을 이용하면 element의 기존 `width`와 `height`을 return 하지만 `Element.getBoundingClientRect()`을 이용하면 최종적으로 rendering된 요소의 width와 height을 return한다. 

=> 예를 들어 기존 `width: 100px`이고, `transform: scale(0.5)`를 통해 크기를 반으로 줄엿다면,` Element.getBoundingClientRect()`는 50을 return 하고, `offsetWidth`는 100을 return 한다. 

=> 우리가 지금 필요한 건, 브라우저에서 실제로 보여지는 height 이니까, `getBoundingClientRect`를 사용해야 한다. 

<br><br>

이제 본격적으로 구현을 해보자 

<br>

`const navbar = document.querySelector('#navbar');`

=> 페이지 내의 `id`가 `navbar`인 요소를 가져온다 .

<br>

```javascript
document.addEventListener('scroll', ()=>{
    // 페이지가 scroll이 될 때마다 해당 부분을 실행해주는 코드
})
```

 <br>

```javascript
document.addEventListener('scroll', ()=>{
    if(window.scrollY > navbarHeight){
        navbar.classList.add('navbar--dark');
    } else {
        navbar.classList.remove('navbar--dark');
    }
})
```

scroll이 될 때, 

`navbar`의 height보다 더 많이 scroll 되었을 경우, `navbar`에 `navbar--dark`class를 추가해주고, 

`narbar`의 height보다 적게 scroll 된 경우, class를 제거해준다. 

<br>

```css
#navbar{
    ~
    transition: all var(--animation-duration) ease-in-out;
}

#navbar.narbar--dark {
    background-color: pink;
    padding: 8px;
}
```
