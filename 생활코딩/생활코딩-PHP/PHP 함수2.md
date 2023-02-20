# 🚩PHP 함수

## 📌 PHP 함수의 형식

User-defined function

```php+HTML
<?php
	function basic(){
        print("아무거나");
        print("아무거나")    
    }

	basic();
?>
```



더하기 함수의 구현

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
  		return $left+$right;
    }
	
	print(sum2(2, 4));
?>
```