# Object

object가 없었다면

```javascript
const name = 'ellie';
const age = 4;
print(name, age);
function print(name, age){
    console.log(name);
    console.log(age);
}
```

data의 양이 많아지면 관리하기도 힘들고, logical 하게 그룹을 묶어서 생각할 수 없음. 

<br><br>

#### Literals and properties

```javascript
function print(person){
    console.log(person.name);
    console.log(person.age);
}

const ellie = {name: 'ellie', age: 4};
print(ellie);
```

```javascript
const obj1 = {};
const obj2 = new Object();
```

위와 같은 방식으로 object를 생성할 수 있다. object는 `{ key : value }` 형식으로 정의된다. key와 value 쌍의 집합체이다. 

<br>

js는 dynamically typed language이기 때문에 동적으로 type이 run-time에 결정되는 언어이다. 

=> 나중에 새로운 property를 추가할 수 있다. 

=> 하지만 이러한 동적인 property의 추가는 나중에 유지보수하기 어려울 수 있다.  

```javascript
const ellie = {name: 'ellie', age: 4};
print(ellie);

ellie.hasJob = true;
```

심지어 나중에 property의 삭제도 가능하다

```javascript
delete ellie.hasJob;
```

<br><br>

#### Computed properties

object의 property는 2가지 방식으로 접근이 가능함.

```javascript
console.log(ellie.name);
console.log(ellie['name']);

ellie.hasJob = true;
ellie['hasJob'] = true;
```

key는 언제나 string type이어야 함. 

<br>

`ellie.name` 방식을 사용하는 경우

=> 코딩하는 그 순간, 그 key에 해당하는 값을 받아오고 싶을 때 

<br>

`ellie['name']`을 사용하는 경우 

=> 정확하게 어떤 key가 필요한지 모를 때, 즉 run-time에서 결정될 때 이를 사용하게 됨. 

```javascript
function printValue(obj, key){
    console.log(obj[key] );
}

printValue(ellie, 'name');
```

=> `printValue`는 인자로 받은 obj의 프로퍼티 중 `key`에 해당하는 프로퍼티를 출력하는 함수인데 어떤 `key`를 입력받을 지 아직 모르기 때문에 `obj[key]` 방식으로 이를 사용해야 한다.

<br><br>

#### Property value shorthand

```javascript
function makePerson(name, age){
    return {
        name, // 원래는 name: name, 인데 이를 생락할 수 있음
        age,
    };
}

const person = makePerson('ellie', 30);
```

js에서는 `key`와 `value`의 이름이 동일하다면, 이를 생략할 수 있음.

=> 이전에 js에서 class가 없었을 때는 위 `makePerson` 같은 함수를 사용했음.

=> 이렇게 다른 기능을 하지 않고 object만을 생성하는 함수들은 대문자로 시작하도록 함수 이름을 지었고, `name: name,` 이 아닌, `this.name = name;` 이런 식으로 쓰도록 했음.

```javascript
function Person(name, age){
    this.name = name;
    this.age = age; 
}
```

하지만 원래는 

```javascript
function Person(name, age){
    this = {};
    this.name = name;
    this.age = age; 
    return this;
}
```

이런식으로 `this`에 대한 코드들이 생략되어있는 것이고, 이러한 함수를 `constructor function`이라고 한다. 

<br><br>

#### in operator

```/javascript
console.log('name' in ellie); // true
```

=> `name`이라는 key가 `ellie`라는 객체 안에 있는지 확인하는 함수 

<br><br>

#### for..in  vs  for..of

```javascript
// for (key in obj)
for(key in ellie){
    console.log(key);
}
```

=> `ellie`라는 객체 안에 있는 key들을 하나씩 출력

<br>

```javascript
// for (value of iterable)
const array = [1, 2, 4, 5];
for(value of array) {
    console.log(value);
}
```

=> 배열, 리스트 같이 순차적으로 iterable한 객체에 대해서 사용

<br><br>

#### Object Cloning 

```javascript
// 7. Fun cloning
// Object.assign(dest, [obj1, obj2, obj3...])
const user = {name : 'ellie', age : '20'};
const user2 = user; 
```

<br>

```javascript
const user3 = {};
for (key in user){
    user3[key] = user[key];
}
// 이렇게 기존 user 객체의 각 key에 접근해서 새로운 object에 하나씩 할당하는 형식
```

기존에는 이렇게기존 `user` 객체의 각 key에 접근해서 새로운 object인 `user3`에 하나씩 할당하는 형식으로 복제했는데

<br>

```javascript
const user4 = {};
Object.assign(user4, user);

// or

const user4 = Object.assign({}, user);
```

이러한 방식으로 cloning 가능 

<br>

복제하려는 객체 source를 `assign()` function에 여러개 전달할 수도 있다. 

```javascript
const fruit1 = { color: 'red'};
const fruit2 = { color: 'blue', size: 'big'};
const mixed = Object.assign({}, fruit1, fruit2);

console.log(mixed.color); // blue
console.log(mixed.size); // big
```

뒤에나오는 객체 source 일수록 동일한 property가 있다면 값을 계속 덮어 씌워줌. 
