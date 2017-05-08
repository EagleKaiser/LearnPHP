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

.. note:: Note

    * Scientific notation can be used like e 
    * If a second variable is declared with the samename|
    the first will be overriden

Booleans
--------

.. code-block:: language
