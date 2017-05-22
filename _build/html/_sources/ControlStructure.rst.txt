Control Structure
=================

Arithmetic Operators
--------------------

.. code-block:: php    
    
    <?php
    echo 8 + 3;
    echo 8 - 3;
    echo 8 * 3;
    echo 8 / 3;
    echo 8 % 3; //modulus
    echo 4 ** 2; //exponentiation four to the power 2
    ?>

Incrementing/Decrementing
-------------------------

.. code-block:: php

    <?php
    $increment = 2;
    echo $increment++."<br>";
    echo $increment."<br>";
    echo ++$increment."<br>";    
    echo $increment--."<br>";
    echo $increment."<br>";
    echo --$increment."<br>"; 
    ?>
    //output:
    //2
    //3
    //4
    //4
    //3
    //2

Assignment Operators
--------------------

.. code-block:: php

    <?php
    $usingSameVar = 5;
    $usingSameVar += 3;
    echo $usingSameVar;
    //output 8
    ?>

String Operators
----------------

.. code-block:: php

    <?php
    $concat = "william";
    $concat .= " shakespear";
    echo $concat;
    ?>

Comparison Operators
--------------------

.. code-block:: php

    <?php
    var_dump(8==8);
    var_dump(8==="8"); //Identicle -type and value
    var_dump(7 <> 8);
    var_dump(7 != 8);
    var_dump(7 !== "8"); //not identicle -type or value
    var_dump(7 > 7);
    var_dump(7 >= 7);
    var_dump(7 < 7);
    var_dump(7 >= 6);
    ?>

Spaceship Operator
------------------

.. code-block:: php

    <?php
    echo 1 <=> 1;
    echo 1 <=> 2;
    echo 2 <=> 1;
    output 0-11
    ?>

Logical Operators
-----------------

.. code-block:: php

    <?php
    $var1 = (6 < 7);
    $var2 = (8 ==8);

    $var3 = true;
    $var4 = false;

    var_dump($var1);
    var_dump($var2);
    var_dump($var3 && $var4);
    var_dump(!$var4);
    ?>

If Statement
------------

.. code-block:: php

    <?php
    $authors = ["charles", "jane", "William"];
    $count = count($authors);
    if($count > 0)
    {
        echo "there is a total of ".$count." authors";
    }
    else 
    {
        echo "there are no authors";
    }
    //output: there is a total of 3authors
    ?>

Else if Statement
-----------------

 .. code-block:: php

    <?php
    $authors = ["charles", "jane", "William"];
    $count = count($authors);
    if($count == 1)
    {
        echo "there is 1 authors";
    }
    elseif($count > 1)
    {
        echo "there is a total of ".$count." authors";
    }
    else 
    {
        echo "there are no authors";
    }
    //output: there is a total of 3authors
    ?>

Switch Statement
----------------

.. code-block:: php

    <?php
    $authors = [];
    $count = count($authors);
    switch($count)
    {
        case 0:
            echo "there are no authors";
            break;
        case 1:
            echo "there is 1 authors";
            break;
        default:
            echo "there is a total of ".$count." authors";
    }
    ?>

.. note:: 

    Without using break other cases after the correct case will be executed

.. code-block:: php

    <?php
    switch (5 <=>7)
    {
        case 1:
            echo "greater than";
            break;
        case 0:
            echo "equal";
            break;
        case -1:
            echo "less than";
    }
    ?>

Tenary Operator
---------------

(exp1)?(espr2):(expr3)

.. code-block:: php

    <?php
    $authors = ["charles", "jane", "William"];
    $count = count($authors);
    $outcome = ($count > 0) ? "Author Total: ".$count : "noAuthors";
    echo $outcome;
    //output: Author Total: 3
    ?>

Null Coalesce
-------------

.. code-block:: php

    <?php
    $authors = ["charles", "jane", "William"];
    $count = count($authors);
    $outcome = $count ? $count : "Count unavailable";
    echo "<br>;
    $outcome = $count ?? "count unavailable";
    echo $outcome;
    //output: 
    //3
    //3
    ?>

.. note:: 

    The second outcome will return itself if valid else it will return count unavailable

While Loop
----------

.. code-block:: php

    <?php
    $readingIsFun = true;
    $i = 0;
    while($i < 5)
    {
        echo "reading is fun"."<br>";
        $i++;
    }
    ?>

For Loop
--------

.. code-block:: php

    <?php
    for($i = 0; $i <5; $i++)
    {
        echo "Reading is fun";
    }
    ?>

Alternate syntax
----------------

.. code-block:: php

    <?php
    $readingIsFun = true;
    $authors = ["charles", "jane", "William"];
    $count = count($authors);
    
    if($count > 0) :
        echo "there is a total of ".$count." authors<br>";
    else :
        echo "there are no authors<br>";
    endif;

    $i = 0;
    while($readingIsFun) :   
        echo "reading is fun"."<br>";
        $readingIsFun = false;
    endwhile;

    for($i = 0; $i <5; $i++) :
        echo "Reading is fun";
    endfor
    //output:
    //there is a total of 3 authors
    //reading is fun
    //Reading is funReading is funReading is funReading is funReading is fun
    ?>

