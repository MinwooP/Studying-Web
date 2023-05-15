# 리액트 고급내용들

<br>

## 마우스 커서 따라 동그라미 따라오도록

```react
export default function AppXY() {
  const [X, setX] = useState(0);
  const [Y, setY] = useState(0);

  return (
    <div 
      className='container'
      onPointerMove={(event) => {
        console.log(event.clientX, event.clientY);
        setX(event.clientX);
        setY(event.clientY);
      }}
    > 
    
    <div 
      className='pointer' 
      style={{transform: `translate(${X}px, ${Y}px)`}}
    />
    </div>
  );
```

<br>

서로 연관이 있는 데이터는 같이 묶어서 관리하는 게 좋음

```react
const [position, setPosition] = useState({x:0, y:0});

  return (
    <div 
      className='container'
      onPointerMove={(event) => {
        console.log(event.clientX, event.clientY);
        setPosition({x: event.clientX, y:event.clientY});
      }}
    > 
```

<br>

> setState와 prev
>
> https://velog.io/@rlaclgns321/setState-%EC%99%80-prev

 <br>

## 중첩 객체 상태 관리

```react
const [person, setPerson] = useState({
    name: '엘리',
    title: '개발자',
    mentor: {
      name: '밥',
      title: '시니어개발자',
    },
  });

setPerson((prev) => ({
            ...prev, 
            metor: {...prev.mentor, title: title }
          }));
```

setPerson을 들여다보면, 우선 `...prev`를 통해  기존 `person`  state에서 `name`, `title`, `mentor`를 가져오고, 여기서도 `...prev.mentor`를 통해 `name`, `title`을 가져오고, 여기서 title만 변경한다. 

> spread 연산자
>
> https://brillme.tistory.com/69
>
> https://paperblock.tistory.com/62
>
> 깊은 복사, 얕은 복사
>
> https://cocobi.tistory.com/156

<br>

-----

5.8부터 어려움,,,,다시 듣고 필기하기

원칙적으로 리액트에서 state는 불변성을 유지해야 한다. 

<br>

> for each, map, filter 
>
> https://paperblock.tistory.com/59

<br>

> 자바스크립트 const

> 배열 push 

<br><br>

리액트 상태 관리를 위한 리액트 hook

Context API => 컴포넌트 간의 공유되는 state 관리 

<br><br>

### Reducer

`const [person, dispatch] = useReducer(personReducer, initialPerson);`

<br><br>

### Immer

Reducer를 쓰더라도 중첩된 객체가 많을 수록 계속 안으로 들어가야 함

=> 이를 위해 Immer 라이브러리

<br>

불변성 상태의 트리를 손쉽게 변경하게 해준다. 

<br>

일반 object를 업데이트 하는 것처럼 사용하지만 immer 내부적으로는 별도의 객체를 만들어서, 원하는 부분만 업데이트해줌. 

<br>

설치 방법

=>cmd 창에 `yarn add immer use-immer`

<br>

이제 새로운 객체를 만들고 중첩된 걸 업데이트 해줄 필요 없이

=>더 직관적으로 실제 객체를 바로 직접적으로 수정하는 것처럼 사용할  수 있음.

`updatePerson((person) => person.mentors.push({ name, title }));`

<br>

우리가 복잡한 상태를 관리하지 않는다면 굳이 immer까지 설치할 필요는 없겠지만,

어플리케이션에 중첩되고 중첩된 객체가 있다면 이를 좀 더 직관적을 사용하고 싶다면, immer를 사용하는게 좋음. 

<br><br>

### Form을 만드는 법

```react
const handleSubmit = (e) => {
    e.preventDefault();
    console.log(form);
  };

return (
    <form onSubmit={handleSubmit}>
        ~
```

`e.preventDefault();`를 실행함으로써 `form`이 제출되었을 때, 페이지가 refresh 되지 않도록 한다. 

<br>

리액트의 철학 => 모든 UI의 업데이트는 상태 변경으로부터 발생해야 한다. 

하지만 form 같은 요소는 사용자가 입력을 해도, 리액트 내부적으로 상태 변경이 이루어지지 않아도 바로 UI 상으로 입력된 것이 보임. 

=> Uncontrolled Component 라고 한다.

=> 우리가 리액트 컴포넌트에서 가지고 있는 상태와   입력되는 요소들이 실시간으로 매칭이 되도록 만들어줘야 함.

```react
export default function AppForm() {
  const [form, setFrom] = useState({ name: '', email: '' });

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(form);
  };

  const handleChange = (e) => {
    const { name, value } = e.target
    setFrom({ ...form, [name]: value });
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor='name'>이름:</label>
      <input
        type='text'
        id='name'
        name='name'
        value={form.name}
        onChange={handleChange}
      />
      <label htmlFor='email'>이메일:</label>
      <input
        type='email'
        id='email'
        name='email'
        value={form.email}
        onChange={handleChange}
      />
      <button>Submit</button>
    </form>
  );
}
```

<br><br>

### 컴포넌트 재사용성

Wrap - components

태그의 속성 값에 데이터를 전달하는게 아니라, 열린 태그와 닫는 태그 중간에 다른 Component 태그를 넣으면, 

이는 그 열린태그의 props로 전달되어, 그 태그 내부 component로 사용할 수 있게 된다. 

<br>

EX1) Navbar

```react
export default function AppWrap() {
  return (
    <div>
      <Navbar>
        <Avatar
          image='https://images.unsplash.com/photo-1527980965255-d3b416303d12?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1160&q=80'
          name='Bob'
          size={200}
        />
        <p>안녕하세요!</p>
      </Navbar>

      <Navbar>
        <p>안녕하세요!</p>
      </Navbar>
    </div>
  );
}

function Navbar({ children }) {
  return <header style={{ backgroundColor: 'yellow' }}>{children}</header>;
}

function Avatar({ image, name, size }) {
  return (
    <div>
      <img
        src={image}
        alt={`${name}'`}
        width={size}
        height={size}
        style={{ borderRadius: '50%' }}
      />
    </div>
  );
}
```

<br>

EX2) Card

<br>

### Context

![image-20230403103716807](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230403103716807.png)

![image-20230403103905459](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230403103905459.png)

data를 Context에 담고 있고, Provider를 통해 data를 잘 보여주는 우산을 만든다.  

Provider도 컴포넌트 => 하위 컴포넌트를 감싸줄 수 있는 부모 우산 컴포넌트

<br>

### 성능개선

예전에 비해 많이는 신경쓰지 않아도 됨.

<br>

리액트는 외부로부터 주입받는 props와 내부 상태 state가 있는데, props와 state 둘 중 하나만 변경이 되어도, 함수형 컴포넌트는 전체가 다시 호출이 됨. 

<br><br>

### 로딩, 에러 처리를 위한 커스텀 훅

 ```react
 import React, { useEffect, useState } from "react";
 import useProducts from './../../hooks/use-products';
 
 export default function Products() {
   const [checked, setChecked] = useState(false);
   const [loading, error, products] = useProducts({salesOnly: checked});
   const handleChange = () => setChecked((prev) => !prev);
 
   if(loading) return <p>Loading...</p>;
 
   if(error) return <p>{error}</p>
   
   return (
     <>
       <input type="checkbox" value={checked} onChange={handleChange} />
       <label htmlFor='checkbox'>Show Only HOT Sale</label>
       <ul>
         {products.map((product) => (
           <li key={product.id}>
             <article>
               <h3>{product.name}</h3>
               <p>{product.price}</p>
             </article>
           </li>
         ))}
       </ul>
     </>
   );
 }
 ```

```react
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

<br>

커스텀 훅은 리액트 컴포넌트와 비슷한데 함수로 만들어야하고, use라는 키워드를 사용해야 하고, 일반 컴포넌트처럼 useState, useEffect, useCallback, useMemo 사용할 수 있지만

UI 컴포넌트는 UI를 반환하지만, 커스텀 훅은 우리가 원하는 데이터를 반환하면 됨.  

<br>

> Hooks는 (함수들은)
>
> 값의 재사용이 아니라 **로직의 재사용**을 위한 것이다. 

=> 커스텀 훅에서 사용되는 데이터는 글로벌로 선언된 것이 아니기 때문에 각 컴포넌트마다 Hooks안의 데이터는 공유되지 않는다. 개별적인 데이터이다. 

<br><br>

### 클래스 형 컴포넌트









