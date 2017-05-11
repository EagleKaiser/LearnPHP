General Types
=============

Comments
--------

.. code-block:: php

    <?php
    // C++ line Comment

    /*
    C-style comment block
    */

    # Shell Style Comment
    ?>

Case Sensitivity
----------------

* Variables - are Case sensitive

    .. code-block:: php

        <?php
        $caseSensitive = "I am unique.";
        $CaseSensitive = "I’m different.";
        echo $caseSensitive;
        echo $CaseSensitive;
        ?>

* Classes - are not case sensitive
    .. code-block:: php
    
        <?php
        class Company {
        // … 
        }
        $c1 = new ComPanY; 
        $c2 = new COMPANY;
        ?>

* Functions - are not case sensitive

    .. code-block:: php

        <?php
        function companyName() {
        // … 
        }
        companyname(); 
        CompanyName(); 
        COMPANYNAME();
        ?>

Integers
--------

.. code-block:: php

    <?php
    $regInt = 1234;
    $octNum = 01234;
    $hexNum = 0xABC;
    $binaryNum = 0b1000;

    var_dump($regInt);
    var_dump($octNum);
    var_dump($hexNum);
    var_dump($binaryNum);
    //output: int(1234) int(668) int(2748) int(8)    
    ?>

Floats
------

.. code-block:: php

    <?php
    $flaot = 1.234;
    $scientific = 0.1234E4;
    $scientific2 = 1234E-4;
    var_dump($flaot);
    var_dump($scientific);
    var_dump($scientific2);
    //output: float(1.234) float(1234) float(0.1234) 
    ?>

.. note:: 

    * Scientific notation can be used like e 
    * If a second variable is declared with the same name the first will be overriden

Booleans
--------

.. code-block:: php

    <?php
    $bool = false;
    $intHasValue = 1;
    $intNoValue = 0;
    $StringHasValue = "abc";
    $StringNoValue = "";

    var_dump($bool);
    var_dump((bool)$intHasValue);
    var_dump((bool)$intNoValue);
    var_dump((bool)$StringHasValue);
    var_dump((bool)$StringNoValue);
    //output: bool(false) bool(true) bool(false) bool(true) bool(false) 
    ?>

.. note:: 

    putting (bool) in front of variables will check if empty or not

Constant
--------

.. code-block:: php

    <?php
    define('NEW_CONSTANT', "Hello new constant ");

    echo NEW_CONSTANT;
    var_dump(NEW_CONSTANT);
    //output: Hello new constant string(19) "Hello new constant " 
    ?>

.. note:: 

    * Constant naming convention in php is having the name of the constant all caps and seperating the words by underscore
    * parameters are define('name', value);
    * Constants can be access by other functions or classes (Glopal variables)

Determine Type
--------------

.. code-block:: php

    <?php
    define('CHECK_CONSTANT', "Yes, I am a constant!");

    $intVar = 1234;
    $stringVar = "I'm a String";
    $boolVar = true;
    $floatVar = 12.34;

    echo is_int($intVar);
    echo is_string($stringVar);
    echo is_bool($boolVar);
    echo is_float($floatVar);

    echo defined('CHECK_CONSTANT');
    ?>

.. note:: 

    If the variable exist these functions will returen 1 otherwise they will return nothing