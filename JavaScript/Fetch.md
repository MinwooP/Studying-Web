## Fetch()

예전처럼 서버 단에서 대신 API를 호출해주기 보다는 클라이언트 단에서 직접 API를 호출하는 경우가 많아지고 있다. 

원격 API를 간편하게 호출할 수 있도록 **브라우저에서 제공**하는 `fetch()` 함수에 대해서 살펴보자.

<br>

#### fetch() 사용법

```javascript
fetch(url, options)
  .then((response) => console.log("response:", response))
  .catch((error) => console.log("error:", error));
```

`fetch()` 함수는 첫 번째 인자로 URL, 두 번째 인자로 옵션 객체를 받고, **Promise** 타입의 객체를 반환합니다. 반환된 객체는, API 호출이 성공했을 경우에는 응답(response) 객체를 resolve하고, 실패했을 경우에는 예외(error) 객체를 reject합니다. 

옵션(`options`) 객체에는 HTTP 방식(method), HTTP 요청 헤더(headers), HTTP 요청 전문(body) 등을 설정해줄 수 있습니다. 

응답(`response`) 객체로 부터는 HTTP 응답 상태(status), HTTP 응답 헤더(headers), HTTP 응답 전문(body) 등을 읽어올 수 있습니다.

참고로 `fetch()` 함수는 엄밀히 말해, 브라우저의 `window` 객체에 소속되어 있기 때문에 `window.fetch()`로 사용되기도 합니다.

<br>

##### GET 호출

`fetch()` 함수는 디폴트로 GET 방식으로 작동하고 GET 방식은 요청 전문을 받지 않기 때문에 옵션 인자가 필요가 없습니다.



















































## 참고

> https://www.daleseo.com/js-window-fetch/