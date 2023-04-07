# Array APIs

#### 배열을 string으로 변환하기

```javascript
// 1. make a string out of an array
{
    const fruits = ['apple', 'banana', 'orange'];

    // mycode
    let stringArray = '';
    fruits.forEach(function(fruit){
        stringArray += fruit;
    })
    console.log(stringArray);

    // using API
    const result = fruits.join();
    console.log(result); // apple,banana,orange
}
```

`join`

=> 배열을 string으로 변환해줌. 





#### string을 배열로 변환하기

```javascript
// 2. make an array out of a string
{
    const fruits = 'apple, banana, cherry, melon'
    const result = fruits.split(',');
    const result2 = fruits.split(',', 2);
}
```

`split(',')`

=> string을  `','`을 기준으로 구분해서 배열로 return 해준다. 



`split(',', 2)`

=> string을  `','`을 기준으로 구분해서 맨 앞 2개의 element만 배열로 return 해준다. 





#### 배열의 순서 거꾸로 바꾸기

```javascript
const array = {1, 2, 3, 4, 5};
const result = array.reverse();
```

=> `result` 뿐만 아니라 `array`의 값도 거꾸로 바뀌어있음. 





#### 특정 element만 제거하기 