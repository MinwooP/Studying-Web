# To do 프로젝트

## 개발환경설정

`yarn create react-app basic`

<br>	

`App.css` 내용 다 삭제

src에 `Components` 라는 폴더 만들기

<br>

컴포넌트별 jsx파일 + css파일(post css를 쓸 것이므로) => 한번에 묶어서 패키지 형태로 관리해줄 것임.	

<br>

`App.js`에 이제 컴포넌트 시작 

```react
export default function App() {
  return (
    <div>
      <TodoList />
    </div>
  );
}
```

<br>

<br>

## 기능구현

##### 할일 목록

<br>

##### 할일 추가하기

```react
<form onSubmit={handleSumit}>
            <input type='text' 
                placeholder='Add Todo' 
                value={text} 
                onChange={handleChange}/>
            <button>Add</button>    
</form>
```

위의 코드를 통해 할일을 입력받는 input과, 전송할 수 있는 버튼 ui를 만들 수 있음

onChange를 통해 value값이 변경되면 `handleChange` 함수를 실행시켜줄 수 있음

`form`의 `onSubmit`을 통해 button이 클릭되어서 정보가 전송되면 `handleSubmit`함수를 실행실행시켜줄 수 있음. 

<br><br>

##### 고유한 id 만들기

uuid라는 라이브러리 사용

`cmd` => `yarn add uuid`

jsx 파일 상단에 import하고 그냥 `uuid4()` 이렇게 사용하면 됨. 	

```react
import {v4 as uuidv4} from 'uuid'

{
    ~
    onAdd({ id: uuid4(), text, status: 'active'});
}
```

<br><br>

##### 할일 삭제하기

Todo 객체 하나에 이제 체크박스도 들어가야 하고, 삭제버튼도 들어가야 하니 별개의 컴포넌트로 만들어주자 !

<br>

휴지통 아이콘

각 리스트 아이템마다 휴지통 버튼 추가, 체크박스로 변경 

그 휴지통 버튼 누르면, todos에서 삭제 	

<br>

리액트 아이콘 사용하기

1. `cmd` => `yarn add react-icons`

2. https://academy.dream-coding.com/courses/player/react/lessons/1436 들어가서 아이콘 검색해서 원하는 아이콘 클릭하면 `FaTrashAlt`가 복사됨.
3.  쓰려는 jsx 파일 상단에 `import {FaTrashAlt} from 'react-icons/fa'`를 쓰고  `<button><FaTrashAlt/></button> ` 같은 방식으로 쓰면 됨 .

<br><br>

## 스타일링

postCSS => create-React-app으로 프로젝트를 만들면, 자동으로 들어있음

<br>

순수 post CSS를 사용할 때도, 색상은 변수로 정의해두는 것이 좋음

`index.css ` => 프로젝트 전반적인 스타일링 css 코드 여기에 정의 

```css
:root {
  --color-bg-dark: #f5f5f5;
  --color-bg: #fdfffd;
  --color-grey: #d1d1d1;
  --color-text: #22243b;
  --color-accent: #f16e03;  
}
```

<br>

```css
body {
  margin: 0
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  width: 100vw;
  height: 100vh;
  display: flex;	
  justify-content: center;
  align-items: center;
}
```

아이템들의 위치를 중간으로 오도록 

<br>

https://cssgradient.io/ 에서 그라데이션을 만들어 body에 적용

```css
body {
  background: rgb(81,87,111);
  background: linear-gradient(106deg, rgba(81,87,111,1) 0%, rgba(60,61,69,1) 100%);;
}
```

<br>

`body`의 바로 자식인 `root` 꾸며주기 

```css
#root 
  width: 100%;
  height: 60%;
  max-width: 500px;
  background-color: var(--color-bg-dark);
  border-radius: 1rem;
  display: flex;
  flex-direction: column;
  
  box-shadow: 9px 11px 21px -5px rgba(0,0,0,0.58);
-webkit-box-shadow: 9px 11px 21px -5px rgba(0,0,0,0.58);
-moz-box-shadow: 9px 11px 21px -5px rgba(0,0,0,0.58); 
}
```

https://cssgenerator.org/box-shadow-css-generator.html 에서 그림자 생성

<br>

=> `index.css`에서 `body`와 `root`에 대한 스타일링을 작성해주었다. 

<br><br>

`overflow: hidden;` => 자식이 부모 요소를 침범하지 않도록?

<br>

```react
className={`${styles.filter} ${filter === value && styles.selected}` } 
```

클래스 이름을 정할 때,  `styles.filter`는 앞에 무조건 쓰고, 뒤에는 현재 전달받은 filter와 각 li의 value값이 같다면 `selected`를 클래스 이름에 덧붙여 쓰도록

<br><br>

#### 입력 폼 스타일링

`TodoList.jsx`에서 section 안의 To do list들을 표시하는 `ul`은 중간에 두고, 새로운 to do를 입력하는 `AddTodo`는 하단에 위치시키고 싶다.

post CSS를 사용하기 위해 

` <section className={styles.container}>` 이런식으로 className에 styles 붙이기 ?

<br>

```css
* { 
  box-sizing: border-box;
}
```

모든 item들이 padding 이나 이런게 합해진 size로 계산이 되도록

<br>

```css
.button {
    cursor: pointer;
}

.button:hover {
    filter: brightness(125%)
}
```

버튼에 마우스가 올라갔을 때, 손바닥 모양으로 바뀌도록, 전체적으로 버튼이 좀 더 환해지도록 

<br>

```css
.icon {
    transition: all 150ms ease-out;
}
```

icon의 변화가 모두 조금씩 천천히 이루어지도록 

<br><br>

checkbox 디자인 

=> accent color를 통해 해결 가능 

`index.css`

```css
body {
    accent-color: var(--color-accent);
}
```

이렇게 body에 accent color를 지정하면, 어떤 input을 사용하든, 기본 브라우저 UI 대신 accent color를 적용해달라고 명시해줄 수 있음

<br>

스크롤바 디자인 => 8.15강 후반부 참고

<br>

### 투두 아이템 저장 => 로컬 스토리지

<br>

```css
.text{
    flex: 1 1 0%;
}
```

grow, shrink ?

<br>



-----

## 졸프 시 쓸만한 리액트 기능들

+ 로딩, 에러 시 화면 부분은 핵심 기능 다 구현하고, 나중에 처리하자. 

+ 5.23강 커스텀 훅 만들기

  커스텀 훅을 이용해 네트워크 통신 후 데이터를 받아오는 함수를 정의하고, 이를 각 졸프 페이지에서  재사용 할 수 있을지 않을까

  ex) 각 페이지에서 식재료 현황 받아오기

```react
import { useEffect, useState } from "react"

export default function useProducts({salesOnly}) { // 커스텀 훅
    const [loading, setLoading] = useState(false);
    const [error, setError] = useState();
    const [products, setProducts] = useState([]);


    useEffect(() => {
        setLoading(true);
        setError(undefined);
    
        fetch(`data/${salesOnly ? 'sale_' : ''}products.json`)
          .then((res) => res.json())
          .then((data) => {
            console.log("데이터를 네트워크에서 받아옴");
            setProducts(data);
          }).catch(e=> setError('에러가 발생했음!'))
          .finally(() => setLoading(false));
    
        return () => {
          console.log("깨끗하게 청소했습니다.");
        };
      }, [salesOnly]);

    return [loading, error, products];
}
```

<br><br>

### 메인 페이지

```react
const [todos, setTodos] = useState([
        {id: '123', text: '장보기', status: 'active'},
        {id: '124', text: '공부하기', status: 'active
    ]);
```

투두 리스트에서 이렇게 할일 데이터들을 배열 안 객체 형태로 관리하는 것처럼,

식재료 현황 데이터도 네트워크 통신을 통해 식재료 배열을 받아와서

각 식재료 = `{id: '123', name: '김치', period: '14', 보관일자: ~~, 탄소량: ~~}` 이렇게 저장?

<br><br>

메인페이지에서 화면에 식재료 item들을 배치할 때, 

냉장고 3단 전체를 flex contatiner로 설정하고, 

`justify-content: flex-start;` 로 설정해 기본 방향을 왼쪽 => 오른쪽으로 설정하고 

`flex-wrap: wrap;`로 설정해 5개 이상 아이템이 있으면 자동으로 다음 줄로 넘어가도록

=> 대신 아이템들의 크기는 일정하게 지정을 해줘야 할듯? 그래야 5개가 다 차면 다음줄로 자동으로 넘어가도록

<br>

#### 식재료 입력 받기 

무언가를 입력받을 때,  `form` 태그와 그 안에 `input` 태그와 `button` 태그 사용 

`input`의 value와 리액트의 state 연결해서 사용하기

```react
if(text.trim().length === 0){
    return;
}
onAdd({id: '고유한값', text, status: 'active'});
setText(''); // input 태그에 입력된 값 없애줌.
```

`text.trim()`을 하는 순간 text의 앞뒤 여백이 다 없어짐

=> `text`에서 공백을 다 제거해도 길이가 0이라면

=> 아무것도 입력하지 않았거나 공백만 입력했다면 서버로 전송되지 않도록 하기

<br>

> 식재료 입력 시,
>
> 유저에게 식재료 텍스트로 입력 받기 => 서버에 식재료 추가 요청
>
> => 서버에서 식재료 현황 새로 받아오기 
>
> => UI 새로 업데이트

> 이런 플로우로 진행되어야 하나? 아니면 로컬 UI에 먼저 추가하고 그 다음 서버에 추가 요청 ?

<br><br>

#### 식재료 삭제 







6
