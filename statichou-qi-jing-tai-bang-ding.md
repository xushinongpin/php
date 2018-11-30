用过一次就已经有记忆没必要再次获取了

```
<?php
if (!function_exists('d')) {
function d($var, ...$moreVars){
    var_dump($var);
    foreach ($moreVars as $m){
        print_r($m);
    }
}
}
class text
{
    protected static $app = ['a','ab','b','ac','c','ad','d','ae','e','af','f','ag'];
    protected static $mytest;

    public static function index($name){
        return static::staticStudy($name);
    }

    protected static function staticStudy($name){
        if(isset(static::$mytest[$name])){
            print_r("|||||||||||||||$name|||||||||||||||||||<br/>");
            return static::$mytest[$name];
        }
        return static::$mytest[$name] = static::$app[$name];
    }
}
echo "<pre/>";
$test = new text;
for ($i=0;$i<10;$i++){
    echo "---------$i----------<br>";
    $data = $test->index($i);
    d($data);
    $data = $test->index($i);
    d($data);
    echo "<hr/>";
    echo "<hr/>";
}
```

输出

```
---------0----------
string(1) "a"
|||||||||||||||0|||||||||||||||||||
string(1) "a"
---------1----------
string(2) "ab"
|||||||||||||||1|||||||||||||||||||
string(2) "ab"
---------2----------
string(1) "b"
|||||||||||||||2|||||||||||||||||||
string(1) "b"
---------3----------
string(2) "ac"
|||||||||||||||3|||||||||||||||||||
string(2) "ac"
---------4----------
string(1) "c"
|||||||||||||||4|||||||||||||||||||
string(1) "c"
---------5----------
string(2) "ad"
|||||||||||||||5|||||||||||||||||||
string(2) "ad"
---------6----------
string(1) "d"
|||||||||||||||6|||||||||||||||||||
string(1) "d"
---------7----------
string(2) "ae"
|||||||||||||||7|||||||||||||||||||
string(2) "ae"
---------8----------
string(1) "e"
|||||||||||||||8|||||||||||||||||||
string(1) "e"
---------9----------
string(2) "af"
|||||||||||||||9|||||||||||||||||||
string(2) "af"

```



