# Position 연습

### relative VS absolute

![image-20230223093754085](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230223093754085.png)



![image-20230223093737161](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230223093737161.png)

<br>

원래 기본 position은 static이다.

여기서, inner1 box1의 position을 **relative**로 바꾸게 되면 

=> 원래 있어야 할 자리를 유지하면서(여기서 유지한다는 것은 주변 요소는 그 자리가 채워져있다고 생각하고 배치되기 때문에 => inner2 박스처럼) 그 자리보다 우리가 지정한 만큼 상대적으로 이동한다. 

```html
<style>
    .box1 .inner1{
		position: relative;
		top: 30px;
		left: 100px;
	}
</style>
```

![image-20230223094516077](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230223094516077.png)

<br><br>

이번에는 inner1 box2의 position을 **absolute**로 바꾸게 되면 

=> 원래 있어야 할 자리에서 빠져나오기 때문에 box2 inner2는 위로 올라오게 되고, inner1 box2는 `body`를 기준으로 배치된다. 

=> absolute를 지정하게 되면, **근접한 부모 요소 중에 기본값인 static이 아닌 부모의 기준에서 움직이기 때문에** 

 => inner1 box2의 부모인 `box`를 먼저 살펴보는데 이 요소는 static이기 때문에 패스하고 한단계 더 올라가서 `outer`를 살펴보고 이 요소도 static이므로 패스하고 결국 `body`까지 올라가서 `body`를 기준으로 맞추게 된다. 

```html
<style>
    .box2 .inner1{
		position: absolute;
		top: 30px;
		left: 100px;
	}
</style>
```

![image-20230223095542318](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230223095542318.png)

<br><br>

정리하자면, 

position의 기본값은 static이고, static일 때는 top, left 같은 position 속성을 써도 아무런 영향이 없고, 

relative는 원래 있던 공간을 유지하면서 그 공간에서 상대적으로 top, left 만큼 이동하고, absolute는 원래 있던 공간을 유지하지 않고 근접한 부모 중에 static이 아닌 부모를 기준으로 상대적으로 배치 된다.  

<br><br>

position이 static, relative, sticky 이면 부모 box를 기준으로 위치 변경이 일어나고

position이 absolute라면, 부모 중 static이 아닌 box를 기준으로 위치 변경이 일어나고

position이 fixed라면, 페이지 상을 기준으로 위치가 배치된다.   

<br>

sticky는 본인의 위치를 유지하다가, 스크롤되어 더 이상 보이지 않는 시점에 페이지에 고정된다.  