# Centering trick

어떤 요소를 수직이나 수평으로 중간에 정렬하는 방법을 알아보자. 

flex-box는 쉽게 정렬이 가능하지만, 다른 경우에 쓸 수 있는 방법들을 알아보자.

<br>

지금 4개의 큰 박스와 그 각 box 안에 들어있는 3개의 inner box와 1개의 text가 있다. 

![image-20230223104433652](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230223104433652.png)

<br>

```html
<body>
    <div class = "box box1">
        <div class ="inner inner1"></div>
    </div>
    
    <div class = "box box2">
        <div class ="inner inner2"></div>
    </div>
</body>
```

```html
<style>
    .box{
        width: 200px;
        height: 100px;
        backgruond-color: beige;
    }
    
    .inner{
        width: 50%;
        height: 50&;
        background-color: blue;
    }

    .inner1{
        
    }
    
    .inner2{
        
    }
    
    .inner3{
        
    }
    
    .inner4{
        
    }
</style>
```

<br><br>

#### 1. margin : auto

![image-20230223105658535](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230223105658535.png)

```html
<style>
    .inner1{
        margin: auto;
    }
</style>
```

div는 block level이라서 한줄에 하나씩만 들어올 수 있고, margin이 자동적으로 보통 오른쪽에 들어가 있다.

=> block level은 한 줄에 하나씩만 들어가야 하기 때문에, 브라우저 상에서 일부러 margin을 넣어주는 것이다. 

=> 그래서 `margin: auto;` 를 이용하게 되면 margin을 오른쪽만이 아닌 골고루 넣어주게 된다. 

=> 하지만 margin은 한 줄에 하나만 들어가기 위한 것이기 때문에 수평적으로만 가운데 정렬이 가능하다.  

<br><br>

#### 2. text-align: center

```html
<style>
    .box2{
        text-align: center; 
    }
    
    .inner2{
        margin: auto;
    }
</style>
```

text-align이라서 text만 정렬될 것 같지만, 다른 요소들도 정렬이 가능하다. 

=> div는 block level이기 때문에, 바깥 box를 `text-align: center` 로 두고, 안쪽 div인 inner2에 `margin: auto`를 줘야 가운데 정렬이 된다. 

=> 하지만, 만약 block level이 예를 들어 button 같은 요소인 경우, 그냥 바깥 box에 `text-align: center` 만 주어도 가능하다. 

<br><br>

#### 3. translate(50%, 50%)

transform을 이용하면 움직이는 것, rotation 하는 것 등이 가능하다.

```html
<style>
    .inner3{
        transform: translate(50%, 50%);
    }
</style>
```

![image-20230223110348719](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230223110348719.png)

<br>

`transform: translate(50%, 50%)` 라는 속성은 해당 요소의 50% 만큼 해당 요소를 이동시킨다는 의미이기 때문에

=> 이렇게 자식 요소가 부모 요소의 절반 크기라면 그냥 50, 50 이렇게 주면 가운데 정렬이 가능하지만

=> 일반적인 경우에서는 이것만으로는 가운데 정렬이 안된다. 

<br>

따라서, 

```html
<style>
    .box{
        position: absolte;
        top: 50%;
        left: 50%;
        width: 200px;
        height: 200px;
    }
</style>
```

여기까지만 본다면 현재 box는 가운데 정렬이 아닌, box의 왼쪽 상단 구석? 꼭짓점? 이 가운데 정렬이 되어있을 것이고, 여기에 `transform: translate(-50%, -50%)`를 추가하면 box가 가운데 정렬이 된다. 

 ```html
 <style>
     .box{
         position: absolte;
         top: 50%;
         left: 50%;
         width: 200px;
         height: 200px;
         transform: translate(-50%, -50%);
     }
 </style>
 ```

<br>

=> 결론적으로, 요소의 위치가 top, left 등으로 결정될 것인데, 추가적으로 `transform: translate(x, y)`를 이용해 요소의 위치를 수정해 정렬을 맞출 수도 있다 !

<br><br>

#### 4. text-centering

text는 비교적 쉽게 할 수 있다.

```html
<style>
    .box4 h1{
        text-align: center;
        line-height: 100px;
    }
</style>
```

hacky한 방법이긴 하지만, `text-align: center`를 통해 수평을 맞추고, `line-height: 100px`를 통해 수직을 정렬할 수 있다.

=> 부모 상자의 크기만큼 `line-height` 값을 주게 되면, 수직적으로 가운데 정렬이 된다. 