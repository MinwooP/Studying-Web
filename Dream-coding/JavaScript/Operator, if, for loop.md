# Operator, if, for loop

## π© Operator

#### π String concatenation

```javascript
// 1. String concatenation
console.log('my' + ' cat');
console.log('1' + 2); // ? 
console.log(`string literals: 1 + 2 = ${1 + 2}`);
```

> string literal μ λ¦¬
>
> => https://kkkdh.tistory.com/entry/JavaScript-Template-Literals-%EC%A0%95%EB%A6%AC

<br><br>

#### π Numeric operators

μ°μ  μ°μ°μ

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

#### πμ¦κ° μ°μ°μ

```javascript
// 3. Increment and decrement operators
let counter = 2;
const preIncrement = ++counter;
// μμ μ½λλ μλμ κ°μ λμμ ν¨
// counter = counter + 1;
// preIncrement = counter ;

const postIncrement = counter++;
// postIncrement = counter;
// counter = counter + 1;

// --λ λκ°μ λ°©μμΌλ‘ μλ λ¨.
```

<br><br>

#### πν λΉ μ°μ°μ

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

#### πλΉκ΅ μ°μ°μ

```javascript
// 5. Comparison operators
console.log(10 < 6);
console.log(10 <= 6);
console.log(10 > 6);
console.log(10 >= 6);
```



#### πλΌλ¦¬ μ°μ°μ

```javascript
// 6. Logical operators: || (or), && (and), ! (not)
const value1 = false;
const value2 = 4 < 2; // false

function check() { // μκ°μ λ­λΉνλ€κ° κ²°κ΅­ trueλ₯Ό return
    for(let i=0; i<10; i++){
        //wasting time
        console.log(':(');
    }
    return true;
}

// || (or) => finds the first truthy value
console.log(`or: ${value1 || value2 || check()}`); // trueλ₯Ό return

// && (and), finds the first falsy 
console.log(`and: ${value1 && value2 && check()}`)
// often used to compress long if-statement
nullableObject && nullableObject.something 

// ! (not)
console.log(!value1);
```

|| (or)

or μ°μ°μλ₯Ό λ³΄λ©΄, valueλ ννμλ€ μ€μμ νλλΌλ trueκ° λλ κ² μμΌλ©΄ trueκ° λ°νμ΄ λ¨. 

=> μ°μ°μμ κ° ν­μ μμμλΆν° κ²μ¬νλ€κ° μ²μμΌλ‘ trueκ° λμ€λ©΄, κ±°κΈ°μ λ©μΆκ³  trueλ₯Ό λ°ν

=> λ§μ½ μμμ `value1 = true;` μλ€λ©΄, check() ν¨μλ μ€νλμ§ μμ κ².  

> κ·Έλμ μ΄λ κ² || μ°μ°μλ‘ μμ κ΅¬μ±ν  λ, μ°μ°μ΄ λ§μ ν¨μλ³΄λ€λ κ°λ¨ν λ³μλ κ°λ¨ν ννμμ ν­μ μμͺ½μ λ°°μΉνλ κ² μ’μ
>
> => λ³μλ€μ΄ λ§μ½ true μΌλλ§, μ°μ°μ΄ λ§μ ν¨μκ° μ€νλ  κ²μ΄κΈ° λλ¬Έ
>
> => μ°μ°μ΄ λ§μ ν¨μλ μ΅λν νΈμΆμ΄ μλλκ² μ’μΌλκΉ

<br>

&& (and)

valueλ ννμ λ€ μ€ νλλΌλ falseκ° λλκ² μμΌλ©΄ falseλ₯Ό return. λ€ trueμ΄λ©΄ trueλ₯Ό return.

=> and μ°μ°μλ λ§μ°¬κ°μ§λ‘ μ°μ°μ΄ λ§μ ν¨μλ³΄λ€λ κ°λ¨ν λ³μλ κ°λ¨ν ννμμ ν­μ μμͺ½μ λ°°μΉνλ κ² μ’μ

<br>

κ·Έλ¦¬κ³  and μ°μ°μλ null μ²΄ν¬ν  λλ λ§μ΄ μ°μ.

`nullableObject && nullableObject.something ` ν΄λΉ μμμμ 

`nullableObject`κ° nullμ΄λ©΄ μλΆλΆμ΄ falseλΌμ λ°λ‘ return νκΈ° λλ¬Έμ λ·λΆλΆμ΄ μ€νμ΄ μλ¨

=> λ°λΌμ `nullableObject`κ° nullμ΄ μλλλ§ μ΄ `nullableObject`μ `something`μ΄λΌλ valueλ₯Ό λ°μμ€κ² λ¨.

<br>

! (not)

not μ°μ°μλ κ°μ λ°λλ‘ λ°κΏμ€λ€.

<br><br>

#### πEquality operator

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

=> typeμ λ³κ²½ν΄μ κ²μ¬λ₯Ό ν¨.

=> stringμΈ `'5'`μ numberμΈ `5`λ₯Ό κ°λ€κ³  νλ¨ν¨.

=> μλ°μ€ν¬λ¦½νΈ μμ§μ "λ¬Έμμ΄μ΄κΈ΄ νλ° μμ λ€μ΄μλ κ±΄ μ«μ 5μμ, κ·Έλ¬λκΉ λκ°μ κ±°μΌ" λΌκ³  νλ¨

<br>

`===`

=> typeμ΄ λ€λ₯΄λ©΄, λ€λ₯΄λ€κ³  νλ¨

=> typeμ΄ κ°κ³ , λ³μλ€μ κ°λ μλ‘ κ°λ€λ©΄ trueλ₯Ό λ°ν 

```javascript
// object equality by reference
```

<br>

κ·Έλ¦¬κ³  equalityλ₯Ό κ³΅λΆν  λ, **object**λ₯Ό λ μ κ²½μ¨μ κ³΅λΆν  νμκ° μμ

=> objectλ λ©λͺ¨λ¦¬μ νμ¬λ  λ, reference ννλ‘ μ μ₯λ¨

=> 



#### π

#### π

