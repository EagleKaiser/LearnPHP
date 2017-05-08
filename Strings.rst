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
    


String functions
----------------