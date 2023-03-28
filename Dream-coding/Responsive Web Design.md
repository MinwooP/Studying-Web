# Responsive Web Design

반응형 웹 디자인 

<br>

반응형 웹 디자인은 무엇인지 ?

왜 웹사이트를 반응형으로 만들어야 하는지?

어떻게 하면 좋은 반응형 웹 사이트를 만들 수 있는지?

<br>

1990년도에는 대부분의 웹 사이트들은 데스크탑 용으로만 만들어졌음.

=> 하지만 요즘에는 다양한 사이즈의 핸드폰, 태블릿 등이 출시되면서 반응형으로 웹 사이트를 만들지 않으면 특정 핸드폰이나 태블릿에서 쓸데없는 공간이 낭비되거나, 아예 화면이 보이지 않는 경우가 발생. 

<br>

웹 사이트를 만들 때 컨텐츠를 물과 같이 만들어라.

> Content Is Like Water

<br>

따라서 Layout을 디자인 할 때,

Fixed-width Layout 보다는, Fluid Layout으로 디자인하라. 

<br>

예전에 Fluid Layout을 만들 때, 

```css
.left{
    float: left;
   	width: 50%
}

.right{
    float: right;
   	width: 50%
}

```

이렇게 float과 `%` value를 이용해서 많이 구현했었는데,  

요즘에는 layout, box를 만들 때 고정된 px value를 사용하지 않고,  

**Flex grid, Flex box, % value, vw, vh** 를 이용해서 layout과 box의 size를 구상함.

=> 이러한 속성 값들만 잘 활용해도 box의 크기 변화에 따라 content가 자동적으로 늘어나거나 즐어들도록 구현 가능

<br>

box의 크기를 계속 줄이거나 키울 때, 크기가 어느 정도 point에 도달하면 layout이 재배치 되는 기능

=> css의 **Media Queries**를 이용해 구현 가능

  <br>

요즘에는 breakpoint가 따로 정해져 있지 않지만

> + mobile => 320px ~ 480px
> + tablet => 768px ~ 1024px
> + desktop => 1024px ~ 

로 하면 무난하게 반응형 웹 디자인을 만들 수 있음.

<br>

**Media Queries**

![image-20230207172010925](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230207172010925.png)

```css
@media screen and (min-width: 800px){
    .container {
        width: 50%;
    }
}
```

=> screen이 최소 width가 800px이면 container의 styling을 width 50%로 해주세요 ~ 라고 하는 것. 



