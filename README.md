## learn php the right way (22)

## ==> what is php?
php stands for Hypertext Preprocessor which is a scripting language mainly used in web development.

## ==> how does php work
<img src="https://i.ibb.co/YcPcJd8/Screenshot-2023-04-17-024353.png" height="200" width="300"/>

## ==> advantages and disadvantages of php

## ==> variable an constant

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


## ==> Data  types and type casting

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




## ==> heredoc and nowdoc


### heredoc

- Heredoc is useful when we need to include a large block of text within our code that contains variable.
- we can use variable in string (example: 3)
- Supports escape sequences and special characters within the string.
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
    
### nowdoc
- we can't use variable in string
- Does not support escape sequences or special characters within the string.

```
<?php
echo <<<'MYCV'
            my name is junaid
        'MYCV'
?>
```


## ==> array
### indexed array
```
1 
----------
<?php
$arr = ['junaid', 'arman', 'hossain', 'saber'];
foreach($arr as $item){
    echo "name: $item <br>";
}
?>
output: 
name: junaid
name: arman
name: hossain
name: saber
```



```
2 indexed array with index number
--------------------------------
<?php
$arr = ['junaid', 'arman', 'hossain', 'saber'];
foreach($arr as $key=> $item){
    echo "$key ------> name----> $item <br>";
}
?>
output:
0 ------> name----> junaid
1 ------> name----> arman
2 ------> name----> hossain
3 ------> name----> saber

```

### associative array

```
<?php
$arr = [
    'name'=> 'junaid',
    'age'=> '24',
    'religion'=> 'islam',
];
foreach($arr as $key=> $item){
    echo "$key----->$item <br>";
}
?>
output:
name----->junaid
age----->24
religion----->islam
```

## ==> operators
## ==> Conditional Statements
## ==> loops
## ==> switch
## ==> File include

| include  | require |
| ------------- | ------------- |
| execution of the script continues when an error occured  | execution of the script stops when an error occured   |
| we will use this | not |

once---- amra ekta file jotobar ei include_once ba require_once kori na keno, just ekbar ei file ti pabe. sobar uporer file ti beshi priority pabe.


## ==> function
there are two types of function in php
1. built-in functions ----- PHP has over 1000 built-in functions that can be called directly, from within a script, to perform a specific task.
2. user Defined Functions

##### we know that php is a loosely type language
```
<?php
function addNumbers(int $a, int $b) {
  return $a + $b;
}
echo addNumbers(5, "5 days");
// since strict is NOT enabled "5 days" is changed to int(5), and it will return 10
?>

// this is a problem, because, function taking invalid parameter
```

##### we can prevent the above problem by using strict. the strict see that is a function taking a valid parameter or not

```
<?php declare(strict_types=1); // strict requirement

function addNumbers(int $a, int $b) {
  return $a + $b;
}
echo addNumbers(5, "5 days");
// since strict is enabled and "5 days" is not an integer, an error will be thrown
?>

```

## ==> variable scope

PHP has three different variable scopes:
    - local
    - global
    - static


#### Variable with global scope:
A variable declared outside a function has a GLOBAL SCOPE and can only be accessed outside a function:
```
<?php
$x = 4; // global scope

function myFunc(){
    echo $x; // generate an error that is Undefined variable $x
}
myFunc();

echo $x; // 4
```
if we want to access x global scope variable within function, we have to use global keyword like this:

```
<?php
$x = 5;
function myFunc(){

    global $x;
    echo $x; // 5
}
myFunc();

echo $x; // 5

```

or we can access as parameter

```
<?php
$x = 5;
function myFunc($x){

    echo $x; // 5
}
myFunc($x);

echo $x; // 5


```

#### Variable with local scope:
A variable declared within a function has a LOCAL SCOPE and can only be accessed within that function:

```
<?php
function myFunc(){
    $x = 10; //local scope

    echo $x; // 10
}
myFunc();

echo $x; // generate an error that is Undefined variable $x

```

#### static keyword
```
<?php
function myFunc(){
    static $x = 0;
    $x++;
    echo $x;
}
myFunc(); // 1
myFunc(); // 2
myFunc(); // 3

```


## ==> Error Handling and Handlers









































