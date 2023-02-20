# Array

비슷한 종류의 데이터를 한곳에 모아서 보관 => 자료구조

어떤 방식, 어떤 형식으로 data를 담느냐에 따라서 여러가지로 구분

<br>

Object와 자료구조의 차이점?

Object는 토끼와 당근이 될 수 있다. 토끼는 귀 두개 라는 프로퍼티가 있을 수 있고, 먹는다, 뛴다 같은 메서드가 들어있을 수 있다. 하지만 당근은 프로퍼티만 가질 수 있다. 비타민 C, 주황색 같은 프로퍼티를 가질 수 있지만, 메서드를 가지지는 못한다. 

=> 이렇게 Object는 서로 연관된 특징과 행동들을 묶어 놓은 것.

=> 그리고 이러한 토끼와 당근 같이 **비슷한 object들을 묶어 놓는 것**을 **자료구조**라고 한다. 

=> 

보통의 type이 있는 언어에서는 한 자료구조 안에 동일한 type의 object들만 담을 수 있다. 하지만 js는 dynamically typed language이므로 type이 동적으로 정의되기 때문에, 한 자료구조 안에 다양한 종류의 data를 담을 수는 있지만, 이런 방식으로 프로그래밍하는 것이 좋지는 않음. 

<br><br>

### 배열

#### 배열의 선언

```javascript
// 1. Declaration
const arr1 = new Array();
const arr2 = [1, 2];
```

<br><br>

#### Index position

```javascript
// 2. Index position
const fruis = ['apple'. 'banana'];
console.log(fruits);
console.log(fruits.length);
console.log(fruits[0]);
console.log(fruits[1]);
console.log(fruits[2]);
console.log(fruits[fruis.length - 1]);
```

<br><br>

#### Looping over an array

```javascript
// 3. Looping over an array
// print all fruits

// a.for
for (let i=0;i<fruits.length;i++){
    console.log(fruits[i]);
}

// b.for of
for(let fruit of fruits) {
    console.log(friut);
}

// c.forEach
fruits.forEach(function(fruit, index, array){
    console.log(fruit, index, array);
})

```

<br><br>

#### add, delete, copy

```javascript
// 4. add, delete, copy
// push : add an item to the end
fruits.push('melon', 'lemon');

// pop : remove an item from the end
fruits.pop();

// unshift : add an item to the beginning
fruits.unshift('grapes');

// shift : remove an item from the beginning
fruits.shift(); 
```

`shift`와 `unshift`는 push, pop보다 느리다. 

<br>

원하는 특정 index의 item을 삭제하는 것도 가능?

```javascript
fruits.splice(1); // 인덱스 1부터 뒤의 item 다 제거	
fruits.splice(1, 1); // 인덱스 1부터 1개 item 제거
fruits.splice(1, 3, 'hi', 'hello'); // 인덱스 1부터 1개 item 제거 후 인덱스 1의 자리부터 'hi'와 'hello' item 추가 
fruits.splice(1, 0,  'hi'); // 인덱스 1의 자리에 item은 제거하지 않고, 'hi' item만 추가 
```

<br>

combine two arrays

```javascript
const newFruits = fruits.concat(fruits2);
```

<br><br>

#### Searching

 ```javascript
 // 5. Searching
 // indexOf: find the index
 console.log(fruits.indexOf('melon'));
 
 // includes
 console.log(fruits.includes(melon))
 
 // lastIndexOf
 console.log(fruits.lastIndexOf('melon'));
 ```

