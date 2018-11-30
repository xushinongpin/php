# 用过一次就已经有记忆没必要再次获取了



有时我们需要在调用对象，类或超类中操作或调用属性和方法。为了帮助实现这一目标，我们可以使用一些我肯定会在某些时候使用的关键字。我们来解释一下：



this  在这个关键字被用于指调用对象，例如：

```
class Person {
    private $age;
    public function __construct($age) {
      $this->age = $age;
    }
}
```

如您所见，构造函数将$ age的值赋予$ this-&gt; age。这意味着，当一个对象创建一个Person类的实例时，该特定对象的age属性将是在实例化期间传递的任何参数。





self  该自关键词是几乎与此相同，但它用于替代类，将只对静态属性和方法的工作。使用self关键字修改属性时，它将影响该类的所有实例。例：

```
<?php
class Person {
    public static $age = 15;

    public function setAge($age){
        self::$age = $age;
    }

    public function printAge(){
        echo self::$age . "<br/>";
    }
}

$x = new Person();
$y = new Person();

$x->setAge(30);
$y->printAge();

$y->setAge(40);
$x->printAge();

输出
30
40
```

在上面的代码片段中，我们定义了一个setAge方法，它将age的static属性设置为一个值，注意我们如何在这里使用self来引用该类的static属性。当我们通过类的实例的任何对象更改静态属性时，它将影响该类的所有实例，请注意上面我如何使用一个对象设置年龄并通过另一个对象打印它。

**Parent**

parent关键字在子类中使用，它用于调用可能在子类中重新定义的超类的实现。例：

```
<?php
class Person {
    private $age;
    private $name;
    public function __construct($age,$name){
        $this->age = $age;
        $this->name = $name;
    }
    protected function printInfo(){
        echo $this->name . "<br/>" . $this->age . "<br/>";
    }
}
class Student extends Person{
    private $school;
    public function __construct($age,$name,$school){
        parent::__construct($age,$name);
        $this->school = $school;
    }
    public function printStudentInfo(){
        parent::printInfo();
        echo $this->school . "<br/>";
    }
}
$x = new Student(20,"Paul","ULA");
$x->printStudentInfo();

输出：
Paul
20
ULA
```







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

self使用例子  -- 取决于定义当前方法所在的类

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



