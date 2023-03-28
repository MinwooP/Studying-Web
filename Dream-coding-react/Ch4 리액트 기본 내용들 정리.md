# Ch4 리액트 기본 내용들 정리

## 🚩CSR

사용자가 html 파일을 받았을 때, 

html 안에는 거의 비어있고(`div id = root`만 body안에 있고, 다른 ui는 없음)

<br>

리액트는 **클라이언트 사이드 렌더링**이기 때문에 

이렇게 비어있는 html을 보내주고, 우리의 코드와 리액트 코드가 함께 브라우저에 전송이 되면서 클라이언트 사이드에서 코드가 동작하면서 우리가 작성한 코드대로 필요한 돔 요소, 브라우저 UI 요소를 동적으로 다이나믹하게 생성해줌. 

<br>

=> 동적으로 클라이언트 상에서, 브라우저 위에서 만들어졌다.   

<br>

실제로 동적으로 만드는 코드는 src 폴더 안에 들어있고, 

`index.js` 파일이 리액트의 시작 포인트 

```react
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

root 에 첫번째로 `App` component를 렌더링한다.

<br>

사용자가 id가 root인 div 태그만 하나 들어있는 html 파일을 받고, 리액트와 소스코드를 다 다운로드 받으면, 브라우저 상에서 id가 root인 요소를 찾아서 root라는 가상의 요소를 만들고, 여기에 App이라는 컴포넌트를 연결해준다. 그러면 리액트가 App 컴포넌트에 들어가서 리턴되는 JSX 문법을 확인한 다음 이런 태그들을 만들어줘야 하는구나 라고 확인하고 브라우저에서 제공하는 createElement 같은 동적으로 돔 요소를 생성할 수 있는 API를 통해서 코드에 정해진 순서대로 해당되는 태그를 동적으로 만들어주는 것.

<br><br>

## 🚩JSX 문법 정리

리액트 컴포넌트를 만들어보자.

<br>

컴포넌트 필수 요건

+ 대문자로 시작하는 함수를 만들 것
+ JSX를 리턴할 것 

<br>

주의할 점

1. JSX를 return시 하나의 태그만 반환해야 함 ! 그 안에 자식태그는 여러개 있어도 되는데 제일 상위의 태그는 하나여야 함.

   => 만약 부모태그는 필요하지 않고 다수의 태그를 반환하고 싶다면 상위에 `<>자식 태그들 </>` 이렇게 비어있는 태그를 반환하면 됨.  

   => 이 태그는 리액트 내부에서 `<Fragment> </Fragment>`로 변환 됨.

<br>

2. class를 지정하고 싶을 때는 `className`을 사용해야 함.

```react
<h1 className='orange'>Hello</h1>
```

<br>

3. javascript 코드를 작성할 때는 중괄호 `{}`를 이용해야 함.

```react
function App() {
    const name = '엘리';
    return (
    	<>
    	<p>{name}</p>
        <img
            style={{ width: '200px', height: '200px'}}
        </>
        </>
    ); 
}
```

<br><br>

리액트는 자바스크립트 라이브러리 !

기존의 html로 어떻게 돔 요소들을 만들어 나갈 수 있는지 

먼저 완벽히 공부하자 !

<br><br>

심화 예제)

```react
function App() {
    const list = ['우유', '딸기', '바나나', '요거트']
    return (
    	<>
        <ul>
            {list.map((item) => (
                <li>{item}</li>
                ))}
        </ul>
        </>
    ); 
}
```

<br>

## 🚩컴포넌트 만들기

`Profile.jsx`

```react
export default function Profile() {
    return (
        <div className="profile">
            <img
                className='photo'
                src='https://images.unsplash.com/photo-1527980965255-'
                alt='avatar'
            />
            <h1>Minwoo Park</h1>
            <p>프론트 엔드 개발자</p>
        </div>
    )
}
```

<Br>

`AppProfile.jsx`

```react
export default function AppProfile() {
  return (
    <>
      <Profile /> 
    </>
  );
}
```

<br>

`index.js`

```react
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <AppProfile />
  </React.StrictMode>
);
```

<br><br>

#### Props 사용하기

```react
export default function Profile({image, name, title, isNew}) {
    return (
        <div className="profile">
            <img
                className='photo'
                src={image}
                alt='avatar'
            />
            {isNew && <span className='new'>New</span>}
            <h1>{name}</h1>
            <p>{title}</p>
        </div>
    )
}
```

```react
export default function AppProfile() {
  return (
    <>
      <Profile
          image='url'
          name='James Kim'
          title='프론트엔드 개발자'
          isNew={true}
      /> 
    </>
  );
}
```

+ 컴포넌트에 속성으로 원하는 key 와 value를 명시하면, `props`라는 객체로 전달된다. 

+ `isNew`가 true일 때만 `span` 태그가 보일 수 있도록 설정한다. 

<br>

#### Component 더 잘게 쪼개기

Profile에 쓰이는 img를 Avatar Component로 나누기

`Profile.jsx`

```react
export default function Profile({image, name, title, isNew}) {
    return (
        <div className="profile">
            <Avatar image={image} isNew={isNew}/>
            <h1>{name}</h1>
            <p>{title}</p>
        </div>
    )
}
```

<br>

 `Avatar.jsx`

```react
export default function Avatar({ image, isNew }) {
  return (
    <div>
      <img className="photo" src={image} alt="avatar" />
      {isNew && <span className="new">New</span>}
    </div>
  );
}
```

<br><br>

#### Event 처리하기

```react
export default function AppProfile() {
  const handleClick (event) => {
    console.log(event);
    alert('버튼이 클릭됨!');
  }

  return (
    <>
      <button onClick={handleClick}>버튼</button>
      <Profile
          image='https://images.unsplash.com/photo-1679937744139-b83f7770148f?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxlZGl0b3JpYWwtZmVlZHw5fHx8ZW58MHx8fHw%3D&auto=format&fit=crop&w=600&q=60'
          name='James Kim'
          title='프론트엔드 개발자'
          isNew={true}
      /> 
```

<br>

#### 내부 상태 관리 State

리액트에서는 UI와 밀접하게 관련이 있는 변수들은 state 라는 곳에 보관 해줘야 함.

=> 일반 로컬 변수로는 실시간으로 변화를 UI 상에서 보여줄 수 없음

<br>

data를 변경이 가능하게 하고, 변경이 될 때마다 UI를 업데이트 해주기 위해서는 

useState를 사용해야 함.

```react
const [number, setNumber] = useState(0);
```

<br>

`Counter.jsx`

```react
export default function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div className='counter'>
            <span className="number">{count}  </span>
            <button 
                className="button"
                onClick={()=>{
                    setCount(count + 1);
                    console.log(count);
                }}
            >
                Add +
                </button>
        </div>
    );
} 
```

이제 버튼을 누를 때마다 count가 1씩 증가할 것이고, 이는 리액트에서 제공해주는 `setCount`를 이용했기 때문에 `count` 변수 값이 변경될 때마다(즉, `setCount`가 실행될 때마다) 리액트가 자동적으로 `Counter()`라는 함수(컴포넌트)를 다시 호출해준다.

다시 호출되면, 다시 반환되는 `return( ~ )`부분에서는  업데이트 된 `count`값이 들어가므로 UI가 전체적으로 업데이트 된다. 

=> 함수가 전달받는 props이 변경되거나 내부의 useState의 상태가 변경되면(`setCount`가 호출되면), 변경된 해당 컴포넌트 함수 전체를 다시 호출한다. 그래서 다시 return ( ) 부분에 있는 돔 요소가 생기는데, 다만 리액트에서는 가상의 돔 요소를 사용하기 때문에 이전의 돔 요소에서 변경된 부분만 업데이트 해준다 ! 
