# π©PHP ν¨μ

## π PHP ν¨μμ νμ

User-defined function

```php+HTML
<?php
	function basic(){
        print("μλ¬΄κ±°λ");
        print("μλ¬΄κ±°λ")    
    }

	basic();
?>
```



λνκΈ° ν¨μμ κ΅¬ν

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