#  CSS Variable 

```html
<style>
        .first-list{
        background-color: thistle;
        color: white;
        margin-left: 16px;
        }
</style>
```

이렇게 hard coding 하는 것은 좋지 않음

=> 상수 변수로 정의하는 게 좋음.

 

```html
<style>
        :root {
            --background-color: thistle;
            --text-color: whitesmoke;
            --base-space: 8px;
        }

        .first-list {
            background-color: var(--background-color);
            color: var(--text-color);
            margin-left: var(--base-space, 8);
        }

        .second-list {
            background-color: var(--background-color);
            color: var(--text-color);
            margin-left: calc(var(--base-space) * 2);
        }
</style>
```







=> media 쿼리를 이용할 때, 즉 모바일 환경일 때 다른 옵션을 이용하고 싶다면

```html
@media screen and (max-width: 768px) {
            :root {
            --background-color: salmon;
            --text-color: blue;
            --base-space: 4px;
            }   
        }
```

