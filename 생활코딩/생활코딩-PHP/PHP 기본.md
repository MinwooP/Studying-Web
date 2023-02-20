## PHP

### 📌PHP의 원리

웹 브라우저의 주소창에 `index.html`을 입력하면

=> 이 요청을 받은 **서버 컴퓨터**의 **웹 서버**라는 소프트웨어가 이 주소를 보고 확장자가 html이므로 웹 서버는 이것을 자기가 직접 처리할 수 있으므로 서버 컴퓨터의 하드디스크나 ssd에 설치되어있는 `htdocs`  디렉토리에서 `index.html` 파일을 읽어서 이를 바로 웹 브라우저에게 전송

=> 웹 브라우저는 받은 `index.html` 파일의 코드를 해석해서 화면에 표시해줌.



웹 브라우저의 주소창에 `index.html`이 아닌, php 확장자를 사용해 `index.php`를 입력하면, 

=> 웹서버는  확장자가 `php`인 파일은 자신의 소관이 아니라는 것을 알기 때문에

=> php 파일을 처리할 수 있는 소프트웨어가 PHP 이기 때문에 이 프로그램에게 처리를 위임

=> PHP 프로그램이 htdocs안에 있는 `index.php` 파일을 열어서 php의 문법에 따라서 해석해서 최종적으로 html을 만들어내는 것. 

=> 그렇게 만들어진 html 파일을 다시 웹서버가 웹브라우저에게 전송



HTML은 정적이다. 

PHP는 동적이다.

=> 원하는 것을 PHP의 문법에 따라 넣어주면, 이에 따라 최종적으로 웹 페이지를 생성해서 전달	

```PHP
<?php
    
    ?>
```

=> PHP의 모든 코드는 최종적으로 사라진다. 



------

### 📌PHP의 데이터 타입 

#### 숫자

#### 문자

```php+HTML
<?php
  echo "Hello "."world";
?>
```

`'` 연산자

+ concatenation operator => 결합 연산자 



-----

### 📌 변수

`$var` 형식으로 변수를 사용할 수 있음

```php+HTML
<?php
    $name = "leezche";
    echo "Lorem ipsum dolor sit amet, consectetur ".$name." adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco ".$name." laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore egoing eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. by ".$name;
    ?>
```





-----

### 📌 URL 파라미터

php파일의 URL을 통해서 입력값을 전달하고, 웹 사이트에서 그 값을 출력하고 싶을  때

=> `127.0.0.1/parameter.php` 

현재 우리가 만들고있는 애플리케이션은 `parameter.php` 라는 이름을 갖고 있는 애플리케이션이다. 이 애플리케이션에 입력 값을 주고 싶다면, 

=> `127.0.0.1/parameter.php?name=egoing`

`parameter.php` 라는 이름의 php 애플리케이션에게 `name = egoing` 이다라는 입력값을 준 것.

=> name이라는 값을 html 파일에서 어떻게 사용하는지

=> `<?php $_GET['변수이름'] ?>`  으로 사용

```php+HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    안녕하세요. <?php echo $_GET['name']; ?>님
  </body>
</html>
```



두 개의 url 입력 값을 전달하고 싶을 때

`127.0.0.1/parameter.php?name=egoing&address=서울`

=> `&` 기호로 연결 

```php+HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    안녕하세요. <?php echo $_GET['address']; ?>에 사시는 <?php echo $_GET['name']; ?>님
  </body>
</html>
```



#### URL 파라미터의 활용

웹 페이지의 하이퍼링크가 연결된 텍스트를 클릭함에 따라 

URL 파라미터인 ID값이 무엇이냐에 따라서 현재 페이지의 제목을 정하는 것 

`index.html`

```php+HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>
    <h1>WEB</h1>
    <ol>
      <li><a href="index.php?id=HTML">HTML</a></li>
      <li><a href="index.php?id=CSS">CSS</a></li>
      <li><a href="index.php?id=JavaScrit">JavaScript</a></li>
    </ol>
    <h2>
      <?php
        echo $_GET['id'];
      ?>
    </h2>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
  </body>
</html>
```



-----

### 📌 PHP 함수의 사용

```php+HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>function</title>
  </head>
  <body>
      
    <h1>function</h1>
    <?php
    $str = "Lorem ipsum dolor sit amet, consectetur adipisicing elit. sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.";
    echo $str;
     ?>
      
     <h2>strlen()</h2>
     <?php
     echo strlen($str);
      ?>
      <h2>nl2br</h2>
      <?php
     echo nl2br($str);
       ?>
  </body>
</html>
```

`nl2br`

+ PHP 함수
+ 문자열의 모든 줄바꿈 앞에 HTML 줄바꿈 태그를 삽입

<br>

##### 함수의 활용 2

```php+HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>
    <h1>WEB</h1>
    <ol>
      <li><a href="index.php?id=HTML">HTML</a></li>
      <li><a href="index.php?id=CSS">CSS</a></li>
      <li><a href="index.php?id=JavaScript">JavaScript</a></li>
    </ol>
    <h2>
      <?php
        echo $_GET['id'];
      ?>
    </h2>
    <?php
    echo file_get_contents("data/".$_GET['id']);
     ?>
  </body>
</html>
```

`file_get_contents( )`

=> 파리미터로 넘겨받은 파일 이름에 해당하는 파일을 열어 데이터를 받아옴 



-----

### 📌 PHP 함수의 제어문

#### 조건문

```php+HTML
<?php
if( $a > $b)
    echo "a is bigger than b";
?>
```



컴퓨터 프로그래밍에서 제일 기본적인 원리

=> 코드가 순차적으로 실행

=> 하지만 조건문을 사용하면 실행되는 흐름을 바꿀 수 있음.



`if (  )` 

+ 위 괄호 안에는 true or false 인 표현식이 들어가야 함



#### 조건문의 활용

```php+HTML
<h2>
    <?php
	if(isset($_GET['id'])){
        echo $_GET['id'];
    } else {
        echo "Welcome";
    }
    ?>
</h2>
```

`isset( var )`

+ `$var` 라는 변수가 set 되었는지를 확인하는 함수

  

#### 반복문

`while문 기본 예제`

```php+HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Loop</title>
  </head>
  <body>
    <h1>while</h1>
    <?php
    echo '1<br>';
    $i = 0;
    while($i < 3){
      echo '2<br>';
      $i = $i + 1;
    }
    echo '3<br>';
     ?>
  </body>
</html>
```





-----

### 📌 배열

```php+HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Array</title>
  </head>
  <body>
    <h1>Array</h1>
    <?php
    $coworkers = array('egoing', 'leezche', 'duru', 'taeho');
    echo $coworkers[1].'<br>';
    echo $coworkers[3].'<br>';
    var_dump(count($coworkers));
    array_push($coworkers, 'graphittie');
    var_dump($coworkers);
    ?>
  </body>
</html>
```

+ 배열 정의

  => `$coworkers = array('egoing', 'leezche', 'duru', 'taeho');`

+ 배열 요소 접근

  => `$coworkers[1]`

+ 배열에 요소 추가

  => `array_push($coworkers, 'graphittie');`



#### 반복문과 배열 활용

디렉토리에 있는 파일의 개수에 따라 목차를 자동적으로 생성해주도록 해보자 !

=> 

디렉토리에 있는 파일들을 배열에 담아, 배열에 담겨있는 원소를 하나씩 꺼내서 이를 이용해서 글 목록을 프로그래밍적으로 만들어보자 !



기존코드

```php+HTML
<ol>
    <li><a href="index.php?id=HTML">HTML</a></li>
    <li><a href="index.php?id=CSS">CSS</a></li>
    <li><a href="index.php?id=JavaScript">JavaScript</a></li>
</ol>
```



배열과 반목문을 이용한 코드 

```php+HTML
<ol>
      <?php
        $list = scandir('./data');
        $i = 0;
        while($i < count($list)){
          if($list[$i] != '.') {
            if($list[$i] != '..') {
              echo "<li><a href=\"index.php?id=$list[$i]\">$list[$i]</a></li>\n";
            }
          }
          $i = $i + 1;
        }
      ?>
</ol>
```



-----

### 📌 PHP 함수의 형식

User defined function

```php+HTML
function basic(){
	print("Lorem ipsum dolor1<br>");
    print("Lorem ipsum dolor2<br>");
}

basic();
```



더하기 함수 예시

```php+HTML
<?php
function sum($left, $right){
	print($left+$right);
	print("<br>");
    }

sum(2,4);
?>



<?php
function sum2($left, $right){
	return $left, $right;
}

print(sum(2,4));
file_put_contents('result.txt', sum(2,4))
?>
```



-----

### 📌 PHP 함수의 활용

자주 쓰이는 로직들을 함수화 => 정리정돈을 위한 수납상자





























