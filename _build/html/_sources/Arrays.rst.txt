Arrays
======

Indexed Arrays
--------------

.. code-block:: php

    <?php
    $firstType = array("charles", "hello", "world", "Array");
    $secondType = ["charles", "hello", "world", "Array"];
    $allValues = [10, 1.3, "hello", true];
    print_r($firstType);
    echo "<br>";
    print_r($secondType);
    echo "<br>";
    print_r($allValues);
    ?>

Associative Arrays
------------------

.. code-block:: php

    <?php
    $authors = array(
    "quarky" => "Charles Dickens",
    10 => "Jane",
    "poetic" => "William",
    "Mark Twain"
    );
    print_r($authors);
    //output: 
    //Array ( [quarky] => Charles Dickens [10] => Jane [poetic] => William [11] => Mark Twain ) 
    ?>

.. note:: 

    Mark Twain will get an index of 11 which is an increment of the integer 10 that we have provided for Jane.

array_key_exists()
------------------

.. code-block:: php

    <?php
    $firstType = array("charles", "hello", "world", "Array");
    $authors = array(
    "quarky" => "Charles Dickens",
    "brilliant" => "Jane",
    "poetic" => "William",
    "Mark Twain"
    );
    echo $firstType[1]."<br>";
    echo $authors["quarky"]."<br>";
    echo array_key_exists(2, $firstType)."<br>";
    echo array_key_exists("poetic", $authors);
    //output:
    //hello
    //Charles Dickens
    //1
    //1
    ?>

in_array()
----------

.. code-block:: php

    <?php
    $firstType = array("charles", "hello", "world", "Array", 13);
    echo in_array("charles", $firstType)."<br>";
    echo in_array("charles", $firstType, true);
    ?>

.. note:: 

    * If value exist in array it will return 1 as true else it will return nothing as false
    * array function's third parameter will indicate if the return type is the same as the search type ex. int == int
    * In this example if we search for 13 int will return true but string "13" will return false 