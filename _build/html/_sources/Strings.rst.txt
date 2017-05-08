Strings
=======

Single Quoted Strings
---------------------

.. code-block:: php

    <?php
    $currency = 'penny';
    $sampleString = 'A $currency saved is a $currency earned.';
    echo $sampleString;
    echo "<br>";
    $misc = 'St. Patrick\'s Day\n';
    echo $misc;
    //output:
    //A $currency saved is a $currency earned.
    //St. Patrick's Day\n
    ?>

Double Quoted Strings
---------------------

.. code-block:: php

    <?php
    $currency = penny;
    $sampleString = "A $currency saved is a $currency earned.";
    echo $sampleString."<br>";

    $var = 2;
    echo "{$var}nd place<br>";
    echo $var."nd place<br>";

    $misc = "St. Patrick\"s <br>Day\n";
    echo $misc;
    //output:
    //A penny saved is a penny earned.
    //2nd place
    //2nd place
    //St. Patrick"s 
    //Day 
    ?>
    


Here Document
-------------

.. code-block:: php

    <?php
    echo <<<EOT
    Be not afraid of greatness;
    some are born great,
    some achive greatness,
    and others have greatness thrust upon them.

                        -William Shakespeare
    EOT;
    ?>
    
.. note:: 

    Do not put a space before or after EOT

print()
-------

.. code-block:: php

    <?php
    print "without parentheses<br>";
    print ("with parentheses<br>");
    echo "can", "'t ", "be used ", "with ", "print";
    //output:
    //without parentheses
    //with parentheses
    //can't be used with print
    ?>

.. note:: 

    last statement can't be done with print

String built in functions
-------------------------

`String library online <http://php.net/manual/en/ref.strings.php>`_ 

Changing Case
~~~~~~~~~~~~~

    .. code-block:: php

        <?php
        $quote = "To be or not to be, that is the question.";
        $quote = strtolower($quote);
        echo $quote."<br>"
        $quote = strtoupper($quote):
        echo $quote
        //output:
        //to be or not to be, that is the question.
        //TO BE OR NOT TO BE, THAT IS THE QUESTION.
        ?>

String length
~~~~~~~~~~~~~

.. code-block:: php

    <?php
    $quote = "To be or not to be, that is the question.";
    $length = strlen($quote);
    echo $length;
    //output: 54
    ?>