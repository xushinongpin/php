**array\_column** - 返回输入数组中某个单一列的值【 只要二维数组指定键的值 】

eg: array\_column\($arr,'key'\);//返回自然排序的数组

```
//指定键的值做为键
array_column($arr,null,'a');
```

**compact** - 建立一个数组，包括变量名和它们的值【 生成比现有的数组集多一维的一个大数组，变量名称作为键】

```
<?php
    $arr = array('a'=>'qb','b'=>'gf','c'=>'re','d'=>'vc');
    $arr1 = array('q'=>'a','w'=>'b');
    $str = 'hahah';
    $str1 = 'qwerty';
    echo "<pre/>";
    print_r(compact('arr','arr1','str','str1'));

    输出
        Array
        (
            [arr] => Array
                (
                    [a] => qb
                    [b] => gf
                    [c] => re
                    [d] => vc
                )

            [arr1] => Array
                (
                    [q] => a
                    [w] => b
                )

            [str] => hahah
            [str1] => qwerty
        )
```

array\_merge-合并一个或多个数组

parse\_str  把查询字符串解析到变量中  eg: "name=Bill&age=60"

array\_unique  去掉重复数据 array\_unique\($data\);

