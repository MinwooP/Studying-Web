### Transformation

```html
<style>
    .box1{
        transform: translateX(100px);
    }
    
    .box2{
        transform: translate(-50px, 20px);
    }

    .box3{
        transform: scale(1.2);
    }

    .box4{
        transform: rotate(45deg);
    }

    .box5{
        transform: translate(100px, 100px) scale(2) rotate(45deg);
    }
</style>
```

`translateX(100px);` : 해당 요소를 수평적으로 100px 오른쪽으로 이동시킨다.

`transform: translate(-50px, 20px)` : 해당 요소를 왼쪽으로 50px, 아래쪽으로 20px 이동시킨다. 

`transform: scale(1.2)` : 해당 요소의 크기를 1.2배 증가시킨다.  

`transform: rotate(45deg)` : 해당 요소를 45도 회전시킨다. 

<br><br>

### Transition

transition을 이용하면 애니메이션 효과를 줄 수 있다. 

```html
<style>
    .box1:hover{
        background-color: blueviolet;
    }
    
    .box2:hover{
        border-radius: 50%;
        background-color: cornflowerblue;
        
        transition: all 2s ease;
    }
    
    .box3:hover{
        border-radius: 50%;
        background-color: cornflowerblue;
        transform: translateX(400px);
    }
</style>
```

transition을 이용하면, 

어떤 property에 적용할 건지 `transition-property`

얼마나 delay를 줄건지 

얼마 기간 동안 할건지  `transition-duration`

어떤식으로 애니메이션을 줄 건지 `transition-timing-funtion`

등을 설정할 수 있다. 



