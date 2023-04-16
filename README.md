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

