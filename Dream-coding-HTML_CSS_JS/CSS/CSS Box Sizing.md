# CSS content의 크기, BOX Sizing

CSS로 스타일링 할 때, 

"사이즈가 이상한데?"

"왜 이렇게 크기가 변했지?"

라는 문제가 있을 때면, 99% **Box Sizing** 문제 ! 

<br>

> margin vs padding
>
> https://dwbutter.com/entry/CSS-margin-padding-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EC%82%AC%EC%9A%A9%EB%B2%95

<br>

### Box Sizing

```html
<head>
     <style>
        .box{
            width: 100px;
            height: 100px;
            background-color: red;
        }

        .inner{
            width: 100%;
            height: 100%;
            background-color: blue;
        }

        .box2{
            padding: 20px;
        }
    </style>
</head>
```

```html
<body>
    <h3>Box without padding</h3>
    <div class="box box1">
        <div class="inner"></div>
    </div>
	
    <h3>Box with padding</h3>
    <div class="box box2">
        <div class="inner"></div>
    </div>

    <h3>Box with padding, border box</h3>
    <div class="box box3"> 
        <div class="inner"></div>
    </div>
</body>
```

바깥 쪽 box는 width,  height 모두 100px로 주고,

안 쪽 box는 부모의 100% width, heigh을 차지하도록 주었다. 

하지만 box2 에는 padding을 20px 주었다. 

![image-20230220130618735](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230220130618735.png)

box에 패딩이 추가되면서, 전체적인 box의 크기가 커졌다.

=> 바깥 box인 box2의 width와 height은 100px로 동일하지만, padding이 20으로 추가되어 전체적인 요소의 크기는 120으로 커진 것. 

<br>

기본적인 box-sizing은 content-box이다.

=> box의 size는 content의 width와 height을 정의하는 것.

<br>

그래서 이렇게 

```html
<style>
    .box{
        width: 100px;
        height: 100px;
        background-color: red;
    }
</style>
```

box의 width와 height을 지정하는 것은 content의 width와 height을 지정하는 것.

 ```html
 <head>
      <style>
         .box2{
             padding: 20px;
             border: 10px solid black;
         }
     </style>
 </head>
 ```

그래서 이렇게 border를 10px로 지정해도

![image-20230220131642375](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230220131642375.png)

content의 width, height 100px과 padding 20px은 변하지 않고 border만 외부에 추가 되는 것.

<br><br>

하지만 간혹 padding이나 border 값을 줄 때, content size안에 포함되게 하고 싶다면,

`box-sizing: border-box;` 값을 주면된다.

=> box size를 결정할 때, content 뿐만 아니라 padding, border 까지 포함해서 결정한다. 

```html
<head>
     <style>
         .box{
            width: 100px;
            height: 100px;
            background-color: red;
        }

        .inner{
            width: 100%;
            height: 100%;
            background-color: blue;
        }

        .box2{
            padding: 20px;
            box-sizing: content-box;
            border: 10px solid black;
        }
         
        .box3{
            padding: 20px;
            box-sizing: border-box;
            border: 10px solid black;
        }
    </style>
</head>

<body>
    <h3>Box without padding</h3>
    <div class="box box1">
        <div class="inner"></div>
    </div>
	
    <h3>Box with padding</h3>
    <div class="box box2">
        <div class="inner"></div>
    </div>

    <h3>Box with padding, border box</h3>
    <div class="box box3"> 
        <div class="inner"></div>
    </div>
</body>
```

![image-20230220132234023](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230220132234023.png)

<br><br>

우리가 box의 사이즈의 width와 height을 지정할 때

`box-sizing: content-box` 라면 content 자체의 width와 height을 결정하기 때문에, 우리가 padding이나 boder를 얼마로 설정하든, content의 size에는 영향을 미치지 않는다.

하지만 `box-sizing: border-box`라면, width와 height 값은 border와 padding까지 포함하기 때문에 content의 크기도 이에 맞춰서 작아진다.

<br>

그리고 우리가 통상적으로 padding을 넣는 것은 box안의 여백을 만들기 위함이기 때문에

**대부분은 border-box를 이용**해서 사용하게 된다 ! 





### 정리

width, height은 box의 크기를 지정하는 것인데, 

content-box 

=> content만 box에 포함하고, border,padding은 box 밖의 영역으로 생각

=> width와 height은 content의 크기를 조정



border-box

=> content, border, padding 까지 box안의 영역으로 생각

=> width와 height은 content, border, padding의 크기를 모두 합친 것





## 참고

https://velog.io/@nalsae/%EB%82%B4%EB%B3%B4%EC%A0%95CSS-%EB%AA%A8%EB%A5%B4%EB%A9%B4-%EA%B3%A4%EB%9E%80%ED%95%9C-box-sizing

