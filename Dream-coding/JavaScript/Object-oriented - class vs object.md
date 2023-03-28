# Object oriented 

class vs object

모든 사물과 물체들을 class로 정의할 수 있는 능력을 갖자 ! 

만약 js에 class나 object가 없다면 우리가 정의한 변수들은 둥둥 떠다녀서 규모가 있는 프로젝트를 진행하기에 어려움

***class는 조금 더 연관있는 data를 한 곳에 묶어놓는 container 같은 것.**

쇼핑몰을 만들 때, 수강신청 페이지를 만들 때 어떻게 클래스를 설계해야 하는지 생각해보자. 

<br>

## Class

#### Class vs Object

Class는 붕어빵을 만들 수 있는 틀이다.

+ template
+ declare once
+ no data in 

=> 클래스를 이용해서 실제로 data를 만들어 넣는 것이 바로 object.

<br>

Object

+ instance of a class
+ created many times
+ data in 

클래스는 메모리에 올라가지 않지만, 객체는 실제로 메모리에 올라감.

<br>

#### Class의 선언

js에서는 class가 추가된 지 얼마 안되었음. 

그러면 그 전까지는 어떻게 개발 ~?

=> js에 클래스가 도입되기 전에는 클래스를 정의하지 않고 바로 object를 만들 수 있었음

=> 그리고 이 object를 만들 때 function을 이용해서 template을 만들 수 있었음.

 <br>

클래스 선언

```javascript
// 1. Class declarations
class Person{
    // constructor
    constructor(name, age){
        // fields
        this.name = name;
        this.age = age;
    }

    // methods
    speak() {
        console.log(`${this.name}: hello!`);
    }
}
```

+ 생성자에 field를 정의

  > 무조건 생성자안에서만 필드 정의가 가능한가 ? 

+ 클래스 내에서의 `this`는 생성된 object를 가리킴. 

<br>

객체 생성

```javascript
const ellie = new Person('ellie', 20);
console.log(ellie.name); 
console.log(ellie.age); 
ellie.speak();
```

<br><br>

#### Getter Setter

```javascript
// 2. Getter and setters
class User {
    constructor(firstName, lastName, age){
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
} 

const user1 = new User('Steve', 'Job', -1);
```

이렇게 사용자가 객체의 data를 아무렇게나 설정할 수 있도록 자율성을 부여한다면, 상식에 맞지 않는 값이 객체의 data가 될 수 있다. 따라서, `getter`와 `setter`를 적절하게 정의해줌으로써 이를 방지할 수 있다. 

<br>

```javascript
// 2. Getter and setters
class User {
    constructor(firstName, lastName, age){
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
} 

const user1 = new User('Steve', 'Job', -1);

get age(){
    return this._age;
}

set age(value){
    if(value<0){
        throw Error('age cna not be negative');
    }
    this._age = value;
}
```

js에서는 이렇게 getter와 setter를 정의하는 순간, 

`this.age`는 메모리에 올라가있는 객체의 `age` 값을 읽어오는 것이 아니라, getter를 호출하게 된다.  

`this.age = age`에서 `=`는 setter를 호출하게 된다.

> 그럼 실제 property는 `age`가 아니라 `_age`가 되는 것인가?

❗❗❗❗❗❗❗ getter, setter는 완전히 이해못했으므로 나중에 꼭 다시 공부하기

<br><br>

#### Public & Private

최근에 추가되어진 개념이라 많은 js 개발자가 사용하고 있지는 않음.

```javascript
// 3. Fields
class Experiment{
    publicField = 2;
    #privateField = 0;
}
const experiment = new Experiment();
console.log(experiment.publicField);
console.log(experiment.privateField); // undefined
```

<br><br>

#### Static

object의 상관없이 class가 가지고 있는 고유한 data나 method가 됨.

=> 들어노는 data에 상관없이 공통적으로 class에서 쓸 수 있는거라면 static과 static method를 이용해서 작성하는 것이 메모리의 사용을 줄여줄 수 있음.

```javascript
// 4. Static
// Too soon to use !
class Article{
    static publisher = 'Dream Coding';
    constructor(articleNumber){
        this.articleNumber = articleNumber;
    }

    static printPublisher(){
        console.log(Article.publisher);
    }
}

const article1 = new Article(1);
const artivle2 = new Article(2);
console.log(Article.publisher);
Article.printPublisher();
```

<br><br>

#### 상속과 다양성

공통적으로 쓰이는 속성을 재사용하면 편하지 않을까 ?

```javascript
// 5. Inheritance
// a way for one class to extend another class. 

class Shape {
    constructor(width, height, color){
        this.width = width;
        this.height = height;
        this.color = color;
    }

    draw(){
        console.log(`drawing ${this.color} color!`);
    }

    getArea(){
        return this.width * this.height;
    }
}

class Rectangle extends Shape{}
class Triangle extends Shape{
    draw(){ // override
        super.draw(); // 부모의 method 호출
        console.log('🚩')
    }
    getArea(){
        return this.width * this.height / 2;
    }
}

const rectangle = new Rectangle(20, 20, 'blue');
rectangle.draw();
console.log(rectangle.getArea());
const triangle = new Triangle(20, 20, 'red');
triangle.draw();
console.log(triangle.getArea());
```

<br><br>

#### instance of 

```javascript
// 6. Class checking: instanceOf
console.log(rectangle instanceof Rectangle); // t
console.log(triangle instanceof Rectangle); // f
console.log(triangle instanceof Triangle); // t
console.log(triangle instanceof Shape); // t
console.log(triangle instanceof Object); // t
```

`A instanceof B`

A object가 B class의 instance인지 아닌지, 즉, A가 B를 통해 만들어진 객체인지를 확인하는 것. 

`console.log(triangle instanceof Object)`  => true

=> 우리가 js에서 만드는 모든 class들은 `Object`를 상속받은 것.

------
