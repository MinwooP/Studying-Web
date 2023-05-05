프로그래밍에서 가장 중요한 것은?

=> 입력, 연산, 출력

<br>

CPU에 최적화된 연산

메모리의 사용을 최소화 하는 것도 중요

<br>

# JavaScript Data Type

-----

## 🚩변수의 선언

**`let` => Mutable variable을 선언할 때**

+ `let`은 ES6에서 추가된 것.

```javascript
let name = 'ellie'
console.log(name);
name = 'hello';
console.log(name);
```

<br>

`let name = 'ellie'` 

=> `let`이라는 키워드를 통해 `name`이라는 변수를 정의하게 되면, 1개의 박스를 가리킬 수 있는 포인터가 생기게 되는 것

=> `name`이라는 변수가 가리키고 있는 메모리 어딘가에 `ellie`라는 값을 저장하는 것.

=> 그리고 추후에 `name` 변수가 가리키고 있는 곳에 다른 값을 넣어서 저장할 수도 있음.

> 어플리케이션을 실행하게 되면, 어플리케이션마다 쓸 수 있는 메모리가 할당됨.이 메모리는 텅텅 비어져있는 box 라고 생각하면 되는데, 어플리케이션마다 쓸 수 있는 box의 개수가 제한적으로 할당되어있다.  

<br>

Block scope

`{ }`를 이용해서 코드를 block 안에 작성하게 되면, block 외부에서는 내부의 내용을 볼 수 없게 됨	

=> global scope 변수는 코드 어느 곳에서나 접근이 가능하지만, block 안에서 정의된 변수는 밖에서 접근이 불가능하다. 

> global scope 변수들은 어플리케이션이 실행되는 순간부터 종료되는 순간까지 항상 메모리에 탑재되어 있기 때문에 최소한으로 쓰는 것이 좋다. class나 함수, if나 for loop 등 필요한 부분에서만 정의해서 사용하는 것이 좋다. 

```javascript
let globName = 'global name';
{
    let name = 'ellie'
    console.log(name);
    name = 'hello';
    console.log(name);
}
console.log(name);
console.log(globName);
```

<br>

> ES6 이전에는 변수의 선언 시`var`를 사용했음. 
>
> `var`의 문제점 
>
> 1. var hoisting 문제
>
>    => move declaration from bottom to top
>
>    => 변수를 어디에 선언했느냐에 상관없이 선언을 항상 맨 위로 끌어올려주는 것. 
>
> 2. var는 block scope이 적용되지 않음. 
>
>    => var는 block을 철저히 무시함.

<br><br>

**`const` => Immutable variable을 선언할 때** 

한번 할당하면 값이 절대 바뀌지 않는 상수

=> 위에서 `let`을 이용해 변수를 선언하면, 이 변수가 메모리 어딘가에 할당된 box를 가리키고 있어서 포인터를 이용해 값을 계속 바꿀 수 있었지만,

 => `const`로 선언된 변수는 이 포인터가 잠겨있다고 생각하면 됨.

=> 변수를 선언함과 동시에 값을 할당한 이후로는, 절대 값을 변경할 수 없음.

<br>

> constant가 좋은 이유
>
> 1. security
>
> 2. thread safety
>
>    => 어플리케이션이 실행되면 한 가지의 프로세스가 할당이 되고,  그 프로세스 안에서는 다양한 thread가 동시에 돌아가는데, 이 다양한 thread들이 동시에 변수에 접근해서 값을 변경할 수도 있는데, 이는 위험하기 때문에 constant 가 안전.
>
> 3. reduce human mistakes

<br>

## 🚩Variable types

어떤 프로그래밍 언어든, Variable type은 크게 

1. Primitive
2. object로 나뉜다.

<br>

### Primitive Type

더 이상 작은 단위로 나눠질 수 없는, single item을 말한다.

=> number, string, boolean, null, undefined, symbol 등이 있음

<br>

##### 📌number

c언어와 java 모두 숫자를 정의하는 data type이 여러개이다. byte, short, long 등등 메모리를 효율적으로 할당하기 위해서. 다행히도(?) js에서는 `number` data type으로 선언하면 된다. 

심지어 그냥 `number`도 없이 `let a = 12;`라고만 써도 된다. 

```javascript
const infinity = 1/0;
const negativeInfinity = -1/0;
const nAn = 'not a number' / 2;
console.log(infinity);
console.log(negativeInfinity);
console.log(nAn);
```

<br>

`const infinity  = 1/0;`

=> 1을 0으로 나누면 무한대가 된다. 

=> **Infinity** 값이 할당됨. 

<br>

`const negativeInfinity = -1/0;`

=> -1을 0으로 나누면 음의 무한대가 된다.

=> **- Infinity** 값이 할당

<br>

`const nAn = 'not a number' / 2;`

=> number가 아닌 string을 number로 나누게 되면, **NAN** 값이 할당

<br>

이렇게 **Infinity, -Infinity, NAN** 이 3개의 값은 특별한 숫자 값이고,

나중에 DOM 요소를 자바스크립트를 이용해서 position을 바꾼다던지 다양한 계산을 해야할 때, 주의하지 않으면 이러한 값들이 나올 수 있음. 그래서 항상 연산할 때 그 값이 정말 valid 한 값인지 확인하고 연산하는 것이 중요함. 

<br>

> **bigInt**
>
> 원래 js에서 number는 (-2^53) ~ 2^53 까지 가능했는데,
>
> `const bigInt = 123141590185011859n;`
>
> => 이렇게 number의 끝에 `n`을 붙이면 `bigInt`로 간주됨.

<br>

##### 📌string

js에서는 한 글자든 여러개의 글자든 모두 string type으로 할당이 됨. 	

```javascript
const char = 'c';
const brendan = 'brendan';
const greeting = 'hello ' + brendan;
console.log(`value: ${greeting}, type: ${typeof greeting}`);
const helloBob = `hi ${brendan}!` 
console.log(`value: ${helloBob}, type: ${typeof helloBob}`);
```

<br>

##### 📌boolean

false : 0, null, undefined, NAN, ' '

true : any other value

```javascript
const canRead = true;
const test = 3 < 1; // false
console.log(`value: ${canRead}, type: ${typeof canRead}`);
console.log(`value: ${test}, type: ${typeof test}`);
```

<br>

##### 📌null과 undefined

null과 undefined는 비슷한 듯 보이지만 다르다.

<br>

**null**

```javascript
let nothing = null;
console.log(`value: ${nothing}, type: ${typeof nothing}`);
```

null이라고 할당하는 경우는 => 명확하게 텅텅 비어있는 empty 값임을 지정하고 싶을 때,

<br>

**undefined**

```javascript
let x;
let y = undefined;
console.log(`value: ${x}, type: ${typeof x}`);
```

반대로 undefined의 경우는 선언은 되었지만, 아무 값도 지정되어있지 않은 상태

=> 그래서 얘는 null처럼 텅텅 비어있는지, 값이 들어가있는지 그런게 정해져 있지 않은 상태

<br>

##### 📌 symbol

나중에 다른 자료구조에서 고유한 식별자가 필요하거나 동시다발적으로 일어날 수 있는 코드에서 우선순위를 주고싶을 때 사용됨

간혹 식별자를 string을 이용해 쓰는 경우도 있는데, string은 다른 모듈이나 다른 파일에서 동일한 string을 썼을 때, 동일한 식별자로 간주 됨

=> 하지만 symbol은 반대로 동일한 id로 symbol을 만들어도 다른 식별자임.

=> symbol은 동일한 string을 작성했어도 다른 symbol로 만들어지기 때문에 *주어지는 string에 상관없이 고유한 식별자를 만들 때 사용됨*

```javascript
const symbol1 = Symbol('id');
const symbol2 = Symbol('id');
console.log(symbol1 === symbol2); => false
```

<br>

##### 📌Dynamic typing

js는 Dynamically typed language 라고 불린다. 

=> c나 java 언어는 statically typed language다. c나 java는 변수를 선언할 때 type도 선언해서 어떤 type인지 결정하지만

=> js는 변수를 선언할 때 어떤 type인지 결정하지 않고, run-time 때, 즉 프로그램이 동작할 때 할당된 값에 따라서 type이 변경될 수 있음을 의미. 

=> js는 run-time 때 변수의 data type이 정해지기 때문에 이로 인한 run-time error가 굉장히 자주 발생함

=> 이 문제점을 해결하고자 **typeScript**가 등장한 것

=> js 위에 type이 올려진 언어

<br><br>

### Object	

single item들을 여러개로 묶어서 한 box로 관리할 수 있게 해주는 것. 

=> function, first-class function 등이 있음.

> javascript에서는 function도 data type 중 하나. 
>
> => "우리 프로그래밍 언어는 first-class function이 지원이 돼 !"
>
> => function도 다른 data type처럼 변수에 할당이 가능하고, 그렇기 때문에 함수의 parameter로 전달이 되고 return type으로도 function을 사용가능, 즉 함수를 return 할수도 있음
>
> => 코틀린의 람다와 비슷한 개념인가 ? 

<br>

```javascript
const ellie = {name: 'ellie', age: 20};
ellie.age = 21;
```

여기서 `ellie`는 `const`로 지정되어있어서, 한번 할당된 object는 다시는 다른 object로 변경이 불가능하다.

=> 하지만 object 안에는 `name`과 `age`라는 변수들이 존재

=> 그래서 `ellie.name`과 `ellie.age` 같은 방식으로 접근하면 name과 age의 포인터가 가리키고 있는 메모리에 다른 값을 할당이 가능

> Q)
>
> 그럼 `let ellie = {name: 'ellie', age: 20};`
>
> 이렇게 객체를 선언하면, `const`가 아니니까 다른 object로 할당이 가능한건가 ?
>
> => 직접 해보니 가능한 것 같다. 
>
> ```javascript
> let user = { name: 'Orange'};
> console.log(user);
> 
> user = {age: 13};
> console.log(user);
> ```

https://medium.com/@1992season/%EB%B3%80%EA%B2%BD-%EA%B0%80%EB%8A%A5%ED%95%9C-%EA%B0%92-%EA%B0%9D%EC%B2%B4-f63750fa7f42



메모리에 값이 저장되는 방식이 Primitive, object type에 따라 다름

+ Primitive의 경우, **value 자체가 메모리에 저장됨**

+ Object의 경우, 크기가 큰 경우가 많기 때문에 메모리에 한번에 다 올리지 않음

  => **object를 가리키는 reference가 메모리에 저장됨**

`const ellie = {name: 'ellie', age: 20};`

=> `ellie`가 `ref`를 가리키고, `ref`는 실제 object를 가리키고 있음

=> `ref`가 실제 object인 `name`과 `age`가 담겨있는 메모리를 가리키는 것

 => `ellie`가 가리키고 있는 포인터는 잠겨서, 다른 object로 변경은 불가능하지만 `name`과 `age`는 변경가능도 그 이유

![image-20230209004501272](C:\Users\alsd2\AppData\Roaming\Typora\typora-user-images\image-20230209004501272.png)



변수

Immutable data types: primitive types, frozen objects(i.e. `object.freeze()`)

Mutable data types: all objects by default are mutable in JS

=>

예를 들어서 primitive type 같은 경우에, 한 번 `'ellie'`라는 string을 정의하게 되면, 이 `ellie`를 통째로 메모리에 올렸다가 다른 string으로 변경은 가능하지만, 이 `ellie`라는 string 자체를 `i`를 빼고 다른 char로 바꾼다던지 하는  data 자체를 변경하는 것은 불가능하다. 

또한 object 중에서도 frozon object는 변경이 불가능하다. 하지만 js에서는 기본적으로는 모든 object는 변경이 가능함. 예를 들어 js에서 array는 mutable data type이다. 