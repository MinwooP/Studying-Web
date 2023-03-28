# Ch4 리액트 기본 내용들 정리

## CSR

사용자가 html 파일을 받았을 때, 

html 안에는 거의 비어있고(`div id = root`만 body안에 있고, 다른 ui는 없음)



리액트는 클라이언트 사이드 렌더링이기 때문에 

이렇게 비어있는 html을 보내주고, 우리의 코드와 리액트 코드가 함께 브라우저에 전송이 되면서 클라이언트 사이드에서 코드가 동작하면서 우리가 작성한 코드대로 필요한 돔 요소, 브라우저 UI 요소를 동적으로 다이나믹하게 생성해줌. 



=> 동적으로 클라이언트 상에서, 브라우저 위에서 만들어졌다.   



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

root 에 첫번째로 App component를 렌더링한다.



사용자가 id가 root인 div 태그만 하나 들어있는 html 파일을 받고, 리액트와 소스코드를 다 다운로드 받으면, 브라우저 상에서 id가 root인 요소를 찾아서 root라는 가상의 요소를 만들고, 여기에 App이라는 컴포넌트를 연결해준다. 그러면 리액트가 App 컴포넌트에 들어가서 리턴되는 JSX 문법을 확인한 다음 이런 태그들을 만들어줘야 하는구나 라고 확인하고 브라우저에서 제공하는 createElement 같은 동적으로 돔 요소를 생성할 수 있는 API를 통해서 코드에 정해진 순서대로 해당되는 태그를 동적으로 만들어주는 것.







