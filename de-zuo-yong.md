当调用函数的时候，具体不知道他到底要分多少部分传过来，那么...就很有用了

```
<?php
    if (!function_exists('dd')) {
        function dd($var, ...$moreVars){
            var_dump($var);
            foreach ($moreVars as $m){
                print_r($m);
            }
        }
    }
    echo "<pre/>";
    $array = array('a','b','p');
    $array1 = array('d','h','o');
    $array2 = array('e','i','n');
    $array3 = array('f','j','m');
    $array4 = array('g','k','l');
    dd($array,$array1,$array2,$array3,$array4);
```

打印出结果就是

```
array(3) {
  [0]=>
  string(1) "a"
  [1]=>
  string(1) "b"
  [2]=>
  string(1) "p"
}
Array
(
    [0] => d
    [1] => h
    [2] => o
)
Array
(
    [0] => e
    [1] => i
    [2] => n
)
Array
(
    [0] => f
    [1] => j
    [2] => m
)
Array
(
    [0] => g
    [1] => k
    [2] => l
)
```



