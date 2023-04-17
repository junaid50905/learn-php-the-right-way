## learn php the right way

### what is php?
php stands for Hypertext Preprocessor which is a scripting language mainly used in web development.

### how does php work
<img src="https://i.ibb.co/YcPcJd8/Screenshot-2023-04-17-024353.png" height="200" width="300"/>

### advantages and disadvantages of php

### variable an constant

#### variable

+++++++++++
```
$name = "";
```

#### constant

++++++++++

constant is writen two way, with const and another is define

connstant variable in php
- constant variable are global variable
- we can't change the constant variable value

###### define(name,value,case_insensitive)
    - Names should be in uppercase letters; name can be start with _(like: _DB)
    - case_insensitive : true- case_insensitive false: case_sensitive(default)
    
    example
    ------------
    define("DB", "localhost");
    echo DB;
    
##### const
    
    example
    -----------
    const DB = "localhost_localhost";
    echo DB;
#### difference between const and define
| const     | define |
| ------------- | ------------- |
| define constant at compile time  | define constant at run time |
| only hold scalar values(int,float,string,bool) or array  | any php valid expression including scalar,array,function |

```
-------------
compile time
-----------
<?php
    $a=10;
if($a===10){
    const X = 13;
}
echo X;
// it will give a syntex error
?>
-----------
run time
-----------
<?php
    $a=10;
if($a===10){
    define("X", 12);
}
echo X;
// output: 12
?>
    
```


### Data  types and type casting

php is called loosly type or dynamicly typed scripting language, because there is no need to write data type with variable.

##### 4 scalar types
    - int
    - float
    - string
    - bool
##### 4 compound type
    - array
    - object
    - callable
    - iterable
##### 2 special types
    - resource
    - null


#### type casting refers to convert one data type to another. PHP supports several type casting methods, including implicit and explicit type casting.

#### implicit type casting / type juggling : php engine automatically convert one data type to another, which is known as implicit type casting
    - echo 2 + 3.4  /// 2.0 + 3.4
    - echo "10junaid" + 10   /// 10 + 10 (because php engine first get 10 and ignore the string then add with 10)
    - echo "junaid10" + 10   /// 0 + 10 (because php engine first get string and php take string as 0 and php does not read 10 that with junaid)
    
    
#### explicit type casting is done by programmer

    syntext
    ------------
    (data type) value
    - echo (int / integer) 3.2111            //// 3
    -(float / double / real) "3.323"       ////3.323
    - (boolean / bool) 32       //// 1
    - (string) 32.32  //"32.32"




## heredoc and nowdoc


### heredoc
    <!-- 1. the syntex of here doc -->
    ```php
    <?php
    echo <<<MYCV
                my name is junaid
            MYCV
    ?>
    ```
    
    <!-- 2. we can use html tag in heredoc -->
    ```php
    <?php
    echo <<<MYCONTENT
                <h3>this is the heading</h3>
                <p>this is the content of the heredoc</p>
            MYCONTENT;
    ?>
    ```
    <!-- 3. we can use variable -->
    ```php
    <?php
    $name = "junaid";
    $age = 24;
    $university = "Uttara University";

    echo <<<MYRESUME
                My name is $name and i am $age old. I am doing BSc in CSE forom $university;

            MYRESUME;

    ?>
    ```
    <!-- 4. we can put the heredoc into a variable -->
    ```php
    <?php
        $content = <<<CONTENT
                        <p>here is the content of the content</p>
                      CONTENT;
                      echo $content;
    
    ?>
    ```









