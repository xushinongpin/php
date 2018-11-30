# 用过一次就已经有记忆没必要再次获取了

有时我们需要在调用对象，类或超类中操作或调用属性和方法。为了帮助实现这一目标，我们可以使用一些我肯定会在某些时候使用的关键字。我们来解释一下：



### **this**  在这个关键字被用于指调用对象，例如：

```
class Person {
    private $age;
    public function __construct($age) {
      $this->age = $age;
    }
}
```

如您所见，构造函数将$ age的值赋予$ this-&gt; age。这意味着，当一个对象创建一个Person类的实例时，该特定对象的age属性将是在实例化期间传递的任何参数。



### self  该自关键词是几乎与此相同，但它用于替代类，将只对静态属性和方法的工作。使用self关键字修改属性时，它将影响该类的所有实例。例：

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



### **Parent **parent关键字在子类中使用，它用于调用可能在子类中重新定义的超类的实现。例：

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

Person类有一个构造函数，它接受age和name的参数，然后我们希望创建一个扩展Person的Student类，但我们仍然希望保留超类的构造，我们如何使用超类的构造函数方法在我们的子类？通过使用parent关键字调用构造函数方法。在上面的例子中，我们的子类构造函数接受age和name参数并将它们传递给超类构造函数，然后它还设置了一个学校，因为它没有在超类中定义。此外，我们在超类上有一个受保护的方法，它打印基本信息，年龄和名称，然后我们在Student类上有一个公共方法，它调用超类的printInfo方法并打印学校名称，你可以通过使用parent关键字从超类中调用一个方法而不是在子类中重新定义它来保存很多行。

### 

### static Static关键字也用于定义类上下文，static关键字用于在从另一个类执行进程时引用调用类的属性，使用此示例将更有意义：

```
<?php
abstract class Student {
    private $age;
    private $name;
    private $school;
    private $type;
    public function __construct($age,$name,$school){
        $this->age = $age;
        $this->name = $name;
        $this->school = $school;
        $this->type = static::studentType();
    }
    protected function studentType(){
        return "Not defined";
    }
    public function printType(){
        echo $this->type . "<br/>";
    }
}
class UniversityStudent extends Student{
    protected function studentType(){
        return "University Student";
    }
}
$x = new UniversityStudent(20,"Paul","ULA");
$x->printType();

输出：
University Student
```

在上面的例子中，我们有一个抽象类Student，构造函数使用在实例化扩展抽象Student类的类时传递的参数来定义年龄，名称和学校属性。现在使用此行static :: studentType（）设置type属性，这意味着它将调用最初实例化对象的类上定义的方法，在上面的示例中，我们将实例化UniversityStudent类，该类扩展抽象的Student类，然后当构造函数方法调用static :: studentType（）方法时，它具体地看起来是在UniversityStudent类中定义的方法，而不是在抽象类中定义的方法。

