## PHP

### πPHPμ μλ¦¬

μΉ λΈλΌμ°μ μ μ£Όμμ°½μ `index.html`μ μλ ₯νλ©΄

=> μ΄ μμ²­μ λ°μ **μλ² μ»΄ν¨ν°**μ **μΉ μλ²**λΌλ μννΈμ¨μ΄κ° μ΄ μ£Όμλ₯Ό λ³΄κ³  νμ₯μκ° htmlμ΄λ―λ‘ μΉ μλ²λ μ΄κ²μ μκΈ°κ° μ§μ  μ²λ¦¬ν  μ μμΌλ―λ‘ μλ² μ»΄ν¨ν°μ νλλμ€ν¬λ ssdμ μ€μΉλμ΄μλ `htdocs`  λλ ν λ¦¬μμ `index.html` νμΌμ μ½μ΄μ μ΄λ₯Ό λ°λ‘ μΉ λΈλΌμ°μ μκ² μ μ‘

=> μΉ λΈλΌμ°μ λ λ°μ `index.html` νμΌμ μ½λλ₯Ό ν΄μν΄μ νλ©΄μ νμν΄μ€.



μΉ λΈλΌμ°μ μ μ£Όμμ°½μ `index.html`μ΄ μλ, php νμ₯μλ₯Ό μ¬μ©ν΄ `index.php`λ₯Ό μλ ₯νλ©΄, 

=> μΉμλ²λ  νμ₯μκ° `php`μΈ νμΌμ μμ μ μκ΄μ΄ μλλΌλ κ²μ μκΈ° λλ¬Έμ

=> php νμΌμ μ²λ¦¬ν  μ μλ μννΈμ¨μ΄κ° PHP μ΄κΈ° λλ¬Έμ μ΄ νλ‘κ·Έλ¨μκ² μ²λ¦¬λ₯Ό μμ

=> PHP νλ‘κ·Έλ¨μ΄ htdocsμμ μλ `index.php` νμΌμ μ΄μ΄μ phpμ λ¬Έλ²μ λ°λΌμ ν΄μν΄μ μ΅μ’μ μΌλ‘ htmlμ λ§λ€μ΄λ΄λ κ². 

=> κ·Έλ κ² λ§λ€μ΄μ§ html νμΌμ λ€μ μΉμλ²κ° μΉλΈλΌμ°μ μκ² μ μ‘



HTMLμ μ μ μ΄λ€. 

PHPλ λμ μ΄λ€.

=> μνλ κ²μ PHPμ λ¬Έλ²μ λ°λΌ λ£μ΄μ£Όλ©΄, μ΄μ λ°λΌ μ΅μ’μ μΌλ‘ μΉ νμ΄μ§λ₯Ό μμ±ν΄μ μ λ¬	

```PHP
<?php
    
    ?>
```

=> PHPμ λͺ¨λ  μ½λλ μ΅μ’μ μΌλ‘ μ¬λΌμ§λ€. 



------

### πPHPμ λ°μ΄ν° νμ 

#### μ«μ

#### λ¬Έμ

```php+HTML
<?php
  echo "Hello "."world";
?>
```

`'` μ°μ°μ

+ concatenation operator => κ²°ν© μ°μ°μ 



-----

### π λ³μ

`$var` νμμΌλ‘ λ³μλ₯Ό μ¬μ©ν  μ μμ

```php+HTML
<?php
    $name = "leezche";
    echo "Lorem ipsum dolor sit amet, consectetur ".$name." adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco ".$name." laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore egoing eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. by ".$name;
    ?>
```





-----

### π URL νλΌλ―Έν°

phpνμΌμ URLμ ν΅ν΄μ μλ ₯κ°μ μ λ¬νκ³ , μΉ μ¬μ΄νΈμμ κ·Έ κ°μ μΆλ ₯νκ³  μΆμ  λ

=> `127.0.0.1/parameter.php` 

νμ¬ μ°λ¦¬κ° λ§λ€κ³ μλ μ νλ¦¬μΌμ΄μμ `parameter.php` λΌλ μ΄λ¦μ κ°κ³  μλ μ νλ¦¬μΌμ΄μμ΄λ€. μ΄ μ νλ¦¬μΌμ΄μμ μλ ₯ κ°μ μ£Όκ³  μΆλ€λ©΄, 

=> `127.0.0.1/parameter.php?name=egoing`

`parameter.php` λΌλ μ΄λ¦μ php μ νλ¦¬μΌμ΄μμκ² `name = egoing` μ΄λ€λΌλ μλ ₯κ°μ μ€ κ².

=> nameμ΄λΌλ κ°μ html νμΌμμ μ΄λ»κ² μ¬μ©νλμ§

=> `<?php $_GET['λ³μμ΄λ¦'] ?>`  μΌλ‘ μ¬μ©

```php+HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    μλνμΈμ. <?php echo $_GET['name']; ?>λ
  </body>
</html>
```



λ κ°μ url μλ ₯ κ°μ μ λ¬νκ³  μΆμ λ

`127.0.0.1/parameter.php?name=egoing&address=μμΈ`

=> `&` κΈ°νΈλ‘ μ°κ²° 

```php+HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    μλνμΈμ. <?php echo $_GET['address']; ?>μ μ¬μλ <?php echo $_GET['name']; ?>λ
  </body>
</html>
```



#### URL νλΌλ―Έν°μ νμ©

μΉ νμ΄μ§μ νμ΄νΌλ§ν¬κ° μ°κ²°λ νμ€νΈλ₯Ό ν΄λ¦­ν¨μ λ°λΌ 

URL νλΌλ―Έν°μΈ IDκ°μ΄ λ¬΄μμ΄λμ λ°λΌμ νμ¬ νμ΄μ§μ μ λͺ©μ μ νλ κ² 

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

### π PHP ν¨μμ μ¬μ©

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

+ PHP ν¨μ
+ λ¬Έμμ΄μ λͺ¨λ  μ€λ°κΏ μμ HTML μ€λ°κΏ νκ·Έλ₯Ό μ½μ

<br>

##### ν¨μμ νμ© 2

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

=> νλ¦¬λ―Έν°λ‘ λκ²¨λ°μ νμΌ μ΄λ¦μ ν΄λΉνλ νμΌμ μ΄μ΄ λ°μ΄ν°λ₯Ό λ°μμ΄ 



-----

### π PHP ν¨μμ μ μ΄λ¬Έ

#### μ‘°κ±΄λ¬Έ

```php+HTML
<?php
if( $a > $b)
    echo "a is bigger than b";
?>
```



μ»΄ν¨ν° νλ‘κ·Έλλ°μμ μ μΌ κΈ°λ³Έμ μΈ μλ¦¬

=> μ½λκ° μμ°¨μ μΌλ‘ μ€ν

=> νμ§λ§ μ‘°κ±΄λ¬Έμ μ¬μ©νλ©΄ μ€νλλ νλ¦μ λ°κΏ μ μμ.



`if (  )` 

+ μ κ΄νΈ μμλ true or false μΈ ννμμ΄ λ€μ΄κ°μΌ ν¨



#### μ‘°κ±΄λ¬Έμ νμ©

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

+ `$var` λΌλ λ³μκ° set λμλμ§λ₯Ό νμΈνλ ν¨μ

  

#### λ°λ³΅λ¬Έ

`whileλ¬Έ κΈ°λ³Έ μμ `

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

### π λ°°μ΄

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

+ λ°°μ΄ μ μ

  => `$coworkers = array('egoing', 'leezche', 'duru', 'taeho');`

+ λ°°μ΄ μμ μ κ·Ό

  => `$coworkers[1]`

+ λ°°μ΄μ μμ μΆκ°

  => `array_push($coworkers, 'graphittie');`



#### λ°λ³΅λ¬Έκ³Ό λ°°μ΄ νμ©

λλ ν λ¦¬μ μλ νμΌμ κ°μμ λ°λΌ λͺ©μ°¨λ₯Ό μλμ μΌλ‘ μμ±ν΄μ£Όλλ‘ ν΄λ³΄μ !

=> 

λλ ν λ¦¬μ μλ νμΌλ€μ λ°°μ΄μ λ΄μ, λ°°μ΄μ λ΄κ²¨μλ μμλ₯Ό νλμ© κΊΌλ΄μ μ΄λ₯Ό μ΄μ©ν΄μ κΈ λͺ©λ‘μ νλ‘κ·Έλλ°μ μΌλ‘ λ§λ€μ΄λ³΄μ !



κΈ°μ‘΄μ½λ

```php+HTML
<ol>
    <li><a href="index.php?id=HTML">HTML</a></li>
    <li><a href="index.php?id=CSS">CSS</a></li>
    <li><a href="index.php?id=JavaScript">JavaScript</a></li>
</ol>
```



λ°°μ΄κ³Ό λ°λͺ©λ¬Έμ μ΄μ©ν μ½λ 

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

### π PHP ν¨μμ νμ

User defined function

```php+HTML
function basic(){
	print("Lorem ipsum dolor1<br>");
    print("Lorem ipsum dolor2<br>");
}

basic();
```



λνκΈ° ν¨μ μμ

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

### π PHP ν¨μμ νμ©

μμ£Ό μ°μ΄λ λ‘μ§λ€μ ν¨μν => μ λ¦¬μ λμ μν μλ©μμ





























