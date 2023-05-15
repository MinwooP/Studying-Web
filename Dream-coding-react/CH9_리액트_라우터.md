# 리액트 라우터

#### 라우팅이란 ?

우리가 주소창에 URL을 입력했을 때, 서버에서 요청된 URL에 해당하는 데이터를 전달해주는 것

> 일반적으로 라우팅은 **사용자가 요청한 URL 또는 이벤트를 해석하고 새로운 페이지로 전환하기 위해 필요한 데이터를 서버에 요청하고 페이지를 전환하는 위한 일련의 행위**

해당하는 페이지로 가기 위해서 새로운 URL을 요청하면 그 URL에 맞는 데이터를 서버에서 다시 보내주고, 클라이언트가 이를 받는 행위 

웹 사이트 내 링크를 클릭하면 주소창의 URL도 바뀌고, 새로운 자원을 받아와 브라우저 안의 내용도 바뀌는 것을 볼 수 있음 

<br>

#### 클라이언트 사이드 라우팅 - CSR

새로운 URL을 입력했을 때, 서버에게 새로운 페이지를 요청하는 것이 아니라 페이지 내에서 업데이트가 필요한 부분만 변경해주는 것, 데이터가 더 필요하다면 서버에서 가져옴

EX) 

Navbar에서 특정 탭 메뉴를 선택했을 때, 페이지의 URL은 업데이트 되지만, 로딩 스피너도 동작하지 않고 페이지가 새롭게 리프레쉬 되는 건 아님. body 부분의 콘텐츠만 변경이 된다. 

개발자 도구의 네트워크 탭을 보면, 새로운 탭 메뉴를 클릭할 때, 완전히 새로운 html을 받아오는 게 아니라, 해당 페이지에서 필요한 데이터를, fetch를 이용해서 데이터만 받아오는 것

=> 페이지 전체가 아닌 필요한 부분만 업데이트 되는 것 

<br>

일반적인 라우팅 - 페이지 전체를 받아오는 것 

CSR - 페이지는 유지하되, 부분적으로 내가 원하는 곳만 컴포넌트를 보여줬다가 숨겼다가 하는 것.

<br>

리액트 라우터를 이용하면 Single Page application을 유지하면서 Multi Page 형태의 장점을 사용할 수 있다. 

=> 무슨 뜻 ?

<br>

------

## 라우터 기본 사용법

##### 1. 환경설정

`yarn add react-router-dom`

<br>

##### 2. 사용

```js
import { createBrowerRouter, RouterProvider}
```

```js
const router = createBrowerRouter([
    {
        path: '/',
        element: <p>Home</p>
        errorElemet: <p>Not Found😅</p>,
    },
    {
        path: '/videos',
        element: <p>Videos</p>
    },
]);

function App(){
    return <RouterProvider router={router} />;
}
```

<br><br>

------



## outlet 사용하기







## param 사용하기









## 참고

https://velog.io/@cgy1024/%ED%8E%98%EC%9D%B4%EC%A7%80-%EB%9D%BC%EC%9A%B0%ED%8C%85-Page-Routing

https://velog.io/@gkfla668/React-%ED%8E%98%EC%9D%B4%EC%A7%80-%EB%9D%BC%EC%9A%B0%ED%8C%85%EC%9D%B4%EB%9E%80

