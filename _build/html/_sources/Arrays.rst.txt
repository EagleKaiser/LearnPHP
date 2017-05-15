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

array_push()
------------

.. code-block:: php

    <?php
    $authors = array("charles", "hello", "world", "Array", 13);
    array_push($authors, "Louisa");
    $authors[] = "Montgomery";
    $authors["Hi"] = "Montgomery";
    print_r($authors);
    //output:
    //Array ( [0] => charles [1] => hello [2] => world [3] => Array [4] => 13 [5] => Louisa [6] => Montgomery [Hi] => Montgomery ) 
    ?>

.. note:: 

    * There are two ways to add elements to an array which are array_push and $array[]= 
    * The second method is prefered because if the array is not declared it will create a new array and add the value as the first parameter

aray_pop (remove lase item)
---------------------------

.. code-block:: php

    <?php
    $authors = array("charles", "hello", "world", "Array");
    $lastValue = array_pop($authors);
    echo $lastValue."<br>";
    print_r($authors);
    //output:
    //Array
    //Array ( [0] => charles [1] => hello [2] => world ) 
    ?>

unset (delete arrray or element from array)
-------------------------------------------

.. code-block:: php

    <?php
    $first = array("charles", "hello", "world", "Array");
    $second = array(
    "quarky" => "Charles Dickens",
    "brilliant" => "Jane",
    "poetic" => "William",
    "Mark Twain"
    );
    unset($first[1], $first[0]);
    unset($second[brilliant]);
    print_r($first);
    echo "<br>";
    unset($first);
    print_r($first);
    echo "<br>";
    print_r($second);    
    ?>

Sorting Arrays
--------------

sort()
~~~~~~

.. code-block:: php

    <?php
    $first = array("charles", "hello", "world", "Array");
    $second = array(
    "quarky" => "Charles Dickens",
    "brilliant" => "Jane",
    "poetic" => "William",
    "Mark Twain"
    );
    sort($first);
    print_r($first);
    echo "<br>";
    sort($second);
    print_r($second);
    //output: 
    //Array ( [0] => Array [1] => charles [2] => hello [3] => world ) 
    //Array ( [0] => Charles Dickens [1] => Jane [2] => Mark Twain [3] => William ) 
    ?>

.. note:: 

    * index values will be reproduced for the sort results
    * by using sort in an associative array all associative key values will be changed int indexed value

asort()
~~~~~~~

.. code-block:: php

    <?php
    $first = array("charles", "hello", "world", "Array");
    $second = array(
    "quarky" => "Charles Dickens",
    "brilliant" => "Jane",
    "poetic" => "William",
    "Mark Twain"
    );
    asort($first);
    print_r($first);
    echo "<br>";
    asort($second);
    print_r($second);
    //output:
    ////Array ( [3] => Array [0] => charles [1] => hello [2] => world ) 
    //Array ( [quarky] => Charles Dickens [brilliant] => Jane [0] => Mark Twain [poetic] => William ) 
    ?>

.. note:: 

    asort preserve original indexes and association array_key_exists

ksort()
~~~~~~~

.. code-block:: php

    <?php
    $second = array(
    "quarky" => "Charles Dickens",
    "brilliant" => "Jane",
    "poetic" => "William",
    "Mark Twain"
    );
    ksort($second);
    print_r($second);
    //output:
    //Array ( [brilliant] => Jane [poetic] => William [quarky] => Charles Dickens [0] => Mark Twain ) 
    ?>

.. note:: 

    ksort will sort based on the index and associative key values

count()
-------

.. code-block:: php

    <?php
    $first = array("charles", "hello", "world", "Array");
    echo count($first). "<br>";
    $authors2 = [
            "Male" => array(
                "Charles" => array("Christmas Carol", "Oliver Twist"),
                "William" => array("Romeo & Juliet", "Richard III"),
                "Mark Twain" => Array("Tom Sawyer", "Huck Finn")
                ),
            "Female" => array(
                "L. M. Montgomery" => array("Anne of Green", "Anne of Avolea"),
                "Louisa May" => array("Litle Women")
                )
            ];
    echo count($authors2)."<br>";
    echo count($authors2, 1); 
    //output:
    //4
    //2
    //16
    ?>

.. note:: 

    In multi dimentional arrays we can use 1 or COUNT_RECURSIVE as a second parameter to count all alements of the arrays

foreach()
---------

.. code-block:: php

    <?php
    $second = array(
    "quarky" => "Charles Dickens",
    "brilliant" => "Jane",
    "poetic" => "William",
    "Mark Twain"
    );
    foreach($authors as $val)
    {
        echo $val."<br>";
    }
    foreach($authors as $key => $val)
    {
        echo $val."(".$key.")<br>";
    }
    //output:
    //Charles Dickens
    //Jane
    //William
    //Mark Twain
    //Charles Dickens(quarky)
    //Jane(brilliant)
    //William(poetic)
    //Mark Twain(0)
    ?>

.. note:: 

    $key and $val are temporary variables

Multi dimentional array
-----------------------

.. code-block:: php

    <?php
    $authors2 = [
            "Male" => array(
                "Charles" => array("Christmas Carol", "Oliver Twist"),
                "William" => array("Romeo & Juliet", "Richard III"),
                "Mark Twain" => Array("Tom Sawyer", "Huck Finn")
                ),
            "Female" => array(
                "L. M. Montgomery" => array("Anne of Green", "Anne of Avolea"),
                "Louisa May" => array("Litle Women")
                )
    ];
    print_r($authors2['Male']['Mark Twain'][1]);
    //output
    //Huck Finn
    ?>
    
.. note:: 

    Remove [] parameters to print previous level

