# Operator, if, for loop

## 🚩 Operator

#### 📌 String concatenation

```javascript
// 1. String concatenation
console.log('my' + ' cat');
console.log('1' + 2); // ? 
console.log(`string literals: 1 + 2 = ${1 + 2}`);
```

> string literal 정리
>
> => https://kkkdh.tistory.com/entry/JavaScript-Template-Literals-%EC%A0%95%EB%A6%AC

<br><br>

#### 📌 Numeric operators

산술 연산자

```javascript
// 2. Numeric operators
console.log(1 + 1); // add
console.log(1 - 1); // substract
console.log(1 / 1); // divide
console.log(1 * 1); // multiply
console.log(5 % 2); // remainder
console.log(2 ** 3); // exponentiation
```

<br><br>

#### 📌증감 연산자

```javascript
// 3. Increment and decrement operators
let counter = 2;
const preIncrement = ++counter;
// 위의 코드는 아래와 같은 동작을 함
// counter = counter + 1;
// preIncrement = counter ;

const postIncrement = counter++;
// postIncrement = counter;
// counter = counter + 1;

// --도 똑같은 방식으로 작동 됨.
```

<br><br>

#### 📌할당 연산자

 ```javascript
 // 4. Assignment operators
 let x = 3; 
 let y = 6;
 x += y; // x = x + y;
 x -= y; // x = x - y;
 x *= y; 
 x /= y;
 ```

<br><br>

#### 📌비교 연산자

```javascript
// 5. Comparison operators
console.log(10 < 6);
console.log(10 <= 6);
console.log(10 > 6);
console.log(10 >= 6);
```



#### 📌논리 연산자

```javascript
// 6. Logical operators: || (or), && (and), ! (not)
const value1 = false;
const value2 = 4 < 2; // false

function check() { // 시간을 낭비하다가 결국 true를 return
    for(let i=0; i<10; i++){
        //wasting time
        console.log(':(');
    }
    return true;
}

// || (or) => finds the first truthy value
console.log(`or: ${value1 || value2 || check()}`); // true를 return

// && (and), finds the first falsy 
console.log(`and: ${value1 && value2 && check()}`)
// often used to compress long if-statement
nullableObject && nullableObject.something 

// ! (not)
console.log(!value1);
```

|| (or)

or 연산자를 보면, value나 표현식들 중에서 하나라도 true가 되는 게 있으면 true가 반환이 됨. 

=> 연산자의 각 항을 앞에서부터 검사하다가 처음으로 true가 나오면, 거기서 멈추고 true를 반환

=> 만약 위에서 `value1 = true;` 였다면, check() 함수는 실행되지 않을 것.  

> 그래서 이렇게 || 연산자로 식을 구성할 때, 연산이 많은 함수보다는 간단한 변수나 간단한 표현식을 항의 앞쪽에 배치하는 게 좋음
>
> => 변수들이 만약 true 일때만, 연산이 많은 함수가 실행될 것이기 때문
>
> => 연산이 많은 함수는 최대한 호출이 안되는게 좋으니까

<br>

&& (and)

value나 표현식 들 중 하나라도 false가 되는게 있으면 false를 return. 다 true이면 true를 return.

=> and 연산자도 마찬가지로 연산이 많은 함수보다는 간단한 변수나 간단한 표현식을 항의 앞쪽에 배치하는 게 좋음

<br>

그리고 and 연산자는 null 체크할 때도 많이 쓰임.

`nullableObject && nullableObject.something ` 해당 수식에서 

`nullableObject`가 null이면 앞부분이 false라서 바로 return 하기 때문에 뒷부분이 실행이 안됨

=> 따라서 `nullableObject`가 null이 아닐때만 이 `nullableObject`의 `something`이라는 value를 받아오게 됨.

<br>

! (not)

not 연산자는 값을 반대로 바꿔준다.

<br><br>

#### 📌Equality operator

```javascript
// 7. Equality
const stringFive = '5';
const numberFive = 5;

// == loose equality, with type conversion
console.log(stringFive == numberFive); // true
console.log(stringFive != numberFive); // false

// === strict equality, no type conversion
console.log(stringFive === numberFive); // false
console.log(stringFive !== numberFive); // true
```

`== `

=> loose equality

=> type을 변경해서 검사를 함.

=> string인 `'5'`와 number인 `5`를 같다고 판단함.

=> 자바스크립트 엔진은 "문자열이긴 한데 안에 들어있는 건 숫자 5잖아, 그러니까 똑같은 거야" 라고 판단

<br>

`===`

=> type이 다르면, 다르다고 판단

=> type이 같고, 변수들의 값도 서로 같다면 true를 반환 

```javascript
// object equality by reference
```

<br>

그리고 equality를 공부할 때, **object**를 더 신경써서 공부할 필요가 있음

=> object는 메모리에 탑재될 때, reference 형태로 저장됨

=> 



#### 📌

#### 📌

