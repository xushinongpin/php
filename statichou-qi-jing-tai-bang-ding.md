用过一次就已经有记忆没必要再次获取了

static使用例子

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

self使用例子

```
class selftest
{
    protected static $mydata = ['a','ab','b','ac','c','ad','d','ae','e','af','f','ag'];
    private static $myself;
    public static function index($name){
        if(isset(self::$myself[$name])){
            return self::$myself[$name].' -||-'.self::$myself[$name];
        }
        return self::$myself[$name] = self::$mydata[$name];
    }
}
echo "<pre/>";
$test = new selftest;
for ($i=0;$i<10;$i++){
    echo "<br>---------$i----------<br>";
    $data = $test->index($i);
    d($data);
    $data = $test->index($i);
    d($data);
}
```

输出

```

---------0----------
string(1) "a"
string(7) "a -||-a"

---------1----------
string(2) "ab"
string(9) "ab -||-ab"

---------2----------
string(1) "b"
string(7) "b -||-b"

---------3----------
string(2) "ac"
string(9) "ac -||-ac"

---------4----------
string(1) "c"
string(7) "c -||-c"

---------5----------
string(2) "ad"
string(9) "ad -||-ad"

---------6----------
string(1) "d"
string(7) "d -||-d"

---------7----------
string(2) "ae"
string(9) "ae -||-ae"

---------8----------
string(1) "e"
string(7) "e -||-e"

---------9----------
string(2) "af"
string(9) "af -||-af"
```



