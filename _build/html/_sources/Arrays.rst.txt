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
    ?>

.. note:: 

    Mark Twain will get an index of 11 which is an increment of the integer 10 that we have provided for Jane.