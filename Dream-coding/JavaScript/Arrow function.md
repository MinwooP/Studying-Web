# Function

우리가 사용하는 프로그램들은 각자 저마다 제공하는 고유의 기능들이 있다. 

이렇게 프로그램 안에서도 각각의 기능을 수행하는 **함수**들이 있다.

절차적 언어는 함수가 프로그램에서 굉장히 중요한 기능을 담당한다.

<br>

js에도 class가 추가되었지만, java 언어처럼 pure한 object oriented가 아니고 ***prototype을 base로 한 가짜의 object oriented 이다***.

=> 무슨 뜻 일까 ? 

어쨋든, js는 **procedural language**이다. 

=> 그래서 js에서 function은 굉장히 중요한 역할을 하기 때문에, function을 sub-program이라고도 부른다. 

<br><br>

#### 함수의 정의

```javascript
// 1. Function declaration
// function name(param1, param2){body... return; }
// one function === one


function log(message){
    console.log(message);
}
log.('Hello'@);  
```

+ 하나의 함수는 하나의 역할만 하도록 
+ naming은 함수가 하는 일을 알 수 있도록 
+ 함수는 js에서 object 이다. 

<br>

js에는 type이 없다 ? 

=> 함수 자체의 interface만 보았을 때, message가 string을 전달해야 하는지 number를 전달해야하는지 명확하지 않음.

=> 이에 반해 typescript에서는 type을 명시하기 때문에 interface만 딱 봐도 어떤 타입의 값이 전달되고, 어떤 타입의 값을 return하는지 파악할 수 있음. 

<br><br>

#### 파라미터

함수에 전달되는 parameter 중 premitive type 같은 경우는 메모리에 value가 그대로 저장되어 있기 때문에 value가 전달이 되고, object 같은 경우는 메모리에 reference가 저장되기 때문에, reference가 전달이 된다. 

```javascript
// 2. Parameters
// premitive parameter => pass by value
// object parameter => pass by reference
	
function changeName(obj){
    obj.name = 'coder';
}

const ellie = { name: 'ellie' };
changeName(ellie);
console.log(ellie);
```

=> 이렇 듯, parameter가 obejct인 경우에는 value가 아닌 reference가 전달이 되기 때문에, 함수 안에서 그 reference를 이용해 object의 값을 변경하게 되면, 변경된 사항이 그대로 메모리에 적용이 됨. 

<br><br>

#### Default Parameters (added in ES6)

```javascript
// 3. Default parameters
function showMessage(message, from){
    if(from === undefined){
        from = 'unknown';
    }
    console.log(`${message} by ${from}`);
}
showMessage('Hi!');
```

원래 이렇게 써야했던 것을 

```javascript
function showMessage(message, from ='unknown'){
    console.log('${message by ${from}');
}
showMessage('Hi!');
```

이제는 이렇게 쓸 수 있다. 

<br><br>

#### Rest Parameters 

```javascript
// 4. Rest parameters 
function printAll(...args){
    for( let i=0;i<args.length;i++){
        console.log(args[i]);
    }
}
printAll('dream', 'coding', 'ellie');
```

이렇게 parameter 앞에 `...`을 붙이면 배열 형태로 전달하겠다는 뜻

<br><br>

#### Local scope

> 밖에서는 안이 보이지 않고, 안에서만 밖을 볼 수 있다. 

자식 함수가 부모 함수 내에서 정의된 변수들을 사용할 수 있는 것 => closure

<br><br>

#### Return a value

함수들은 기능을 수행한 다음 값을 return 할 수 있음. 

return문이 없는 함수들은 `return undefined`가 생략되어 있는 것.

```javascript
// Return a value
function sum(a, b){
    return a+b;
}
const result = sum(1, 2); // 3
console.log(`sum: ${sum(1, 2)}`);
```

<br>

가끔 Early return을 해라, Early exit을 해라 하는 상황이 있을 수 있음

=> 조건이 맞지 않을 때는 함수를 빨리 종료하고, 조건이 맞을 때만 그 다음의 로직들을 실행하는 것이 좋음

```javascript
// early return
function upgradeUser(user){
    if(user.point <= 10){
        return;
    }
    // long upgrade logic...
}
```

<br>

지금까지는 함수를 어떻게 선언할 수 있는지를 알아봤다. 

이제는 function expression에 대해서 알아보자. 

<br><br>

#### 📌 First class function

```javascript
// First-class function
// functions are treated like any other variable
// can be assigned as a value to variable
// can be passed as an argument to other functions
// can be returned by another function 
```

함수는 다른 변수와 마찬가지로 변수에 할당이 되고, 다른 함수의 인자로 전달이 되며, 다른 함수의 return 값으로도 사용이 가능하다. 

이를 가능하게 하는 것이 => Funtion expression : 함수 표현식 

<br>

##### Function expression

```javascript
const print = function() {
    console.log('print');
}
```

함수를 선언함과 동시에 변수에 함수를 할당하는 것을 볼 수 있다. 

이렇게 function의 이름은 선언하지 않고, `function`이라는 키워드와 파라미터와 body만 정의

=> 이렇게 이름이 없는 함수를 anonymous function이라고 부른다. 

=> 원한다면 함수의 이름을 작성할 수도 있음 ! => 이는 named function이라고 한다.  

=> 이렇게 변수에 함수를 할당한다면 변수를 함수 호출하듯이 호출할 수 있다.

```javascript
print();
```

<br>

함수가 할당된 변수를 다른 변수에 할당해서, 그 변수를 호출하는 것도 가능하다.

```javascript
const printAgain = print;
printAgain();
```

<br>

그리고 기존의 일반적인 함수를 변수에 할당해도 이를 호출할 수 잇음

```javascript
function sum(a, b){
    return a+b;
}

const sumAgain = sum;
console.log(sumAgain(1, 3));
```

<br>

+ a function declaration can be called earlier than it is defined. (hoisted)

  => 일반적인 함수 정의는 코드 순서상으로 그 함수가 정의되기 전에 호출이 가능하다.

  => javascript engine이 함수 선언을 맨 위로 올려주기 때문 

+ a function expression is created when the execution reaches it

  => 함수 표현식은 실행이 되어야 생성된다. 

  => 함수 표현식은 변수에 할당된 다음부터 호출이 가능하다.   

<br><br>

##### Callback function using function expression

함수를 인자로 전달해서,

"너가 상황에 맞으면 전달된 함수를 불러 ! " 라고 전달하는 것을 call back funtion이라고 한다. 

<br>

즉, 2가지의 call back funtion들이 parameter로 전달되어서 

전달된 인자 answer이 정답일 때는 `printYes()`를 호출하고, 정답이 아니면, `printNo()`를 호출한다.

```javascript
// 2. Callback function using function expression
function randomQuiz(answer, printYes, printAll){
    if(answer === 'love you'){
        printYes();
    } else{
        printNo();
    }
}

// anonymous function
const printYes = function(){
    console.log('yes!');
}

// named function
const printNo = function print(){
    console.log('no!');
}

randomQuiz('wrong', printYes, printNo);
```

+ `printYes`에는 이름이 없는 익명함수가 쓰였고, `printNo`에는 `print`라는 이름이 지정되어 있다. 

  => 이렇게 function expression에서 이름을 쓰는 경우는 디버깅을 할 때, ***debugger의 stack trace에 함수 이름이 나오도록 하기 위해*** 쓰는 거임. 

<br><br>

##### Arrow function

함수를 굉장히 간결하게 만들어 줌. 

항상 익명함수임.  

```javascript
// Arrow function
const simplePrint = function(){
    console.log('simplePrint!');
}
```

이렇게 써야했던 함수 표현식을

```javascript
const simplePrint = () => console.log('simplePrint!');
```

arrow function 형식으로 이렇게 정의할 수 있다. 

<br>

```javascript
const add = function(a, b){
    return a+b;
}

const add = (a, b) => a + b; 


const simpleMultipy = (a,b) => {
    // do something more	
    return a*b;
};
```

<br>=>

함수 표현식을 익명함수 또는 named function으로 정의할 수 있고, 아니면 arrow function으로도 정의할 수 있다.	

<br><br>

##### IIEE

Immediately Invoked Funtion Expression

선언함과 동시에 바로 호출하려면

=> 

함수의 선언을 괄호로 묶은 다음 함수를 호출하듯이 끝에 `();` 더해주면 함수가 호출됨.

```javascript
(function hello(){
    console.log('IIFE');
})();
```

