Functions
=========

What is a Function
------------------

* Block of code 
* Performs a specific task 
* Used throughout your program

.. code-block:: php

    <?php
    function createName($parameter, $anotherParameter) 
    {
     //… perform some function here 
    }
    ?>

Creating/Calling a function 
---------------------------

.. code-block:: php

    <?php
    listOfBooks();

    function listOfBooks()
    {
        echo "Hamlet<br>";
        echo "Romeo and Juliet<br>";
    }
    //output: Hamlet
    //Romeo and Juliet 
    ?>

.. code-block:: php

    <?php
    function bookByAuthorYear($authorName, $year)
    {
        echo $year;
        echo "\n";
        echo $authorName;
    }
    $authorName = "William Shakespeare";
    bookByAuthorYear($authorName, 1910);
    ?>

Passing/Default parameters
--------------------------

.. code-block:: php

    <?php
    function bookByAuthorYear($tempAuthorName, $tempYear = 1910)
    {
        echo $tempYear;
        echo "<br>";
        echo $tempAuthorName;
        echo "<br>";
    }
    $year = 1920;
    $authorName = "William Shakespeare";
    bookByAuthorYear($authorName);
    bookByAuthorYear($authorName, $year);
    //output:
    //1910
    //William Shakespeare
    //1920
    //William Shakespeare
    ?>

.. note:: 

    All required parameters shoud be at the begining of the function parameter and defaults should be at the end.


Returning Values
----------------

.. code-block:: php

    <?php
    function bookByAuthorYear($authorName)
    {
        echo $authorName;        
    }
    function getAuthor()
    {
        return "William Shakespeare";
    }
    bookByAuthorYear(getAuthor());
    //output: William Shakespeare    
    ?>

Variable Functions
------------------

.. code-block:: php

    <?php
    function getAuthor()
    {
        echo "Charles Dickens";        
    }
    $variableFunctionName = "getAuthor";
    $variableFunctionName();
    //output: Charles Dickens
    ?>


Variable Scope
--------------

.. code-block:: php

    <?php
    $authorName = "William Shakespeare";
    function setAuthorName()
    {
        $authorName = "Charles Dickens";
        echo $authorName;
    }
    setAuthorName();
    echo "<br>";
    echo $authorName;
    //output: 
    //Charles Dickens
    //William Shakespeare
    ?>

Function Global Scope
---------------------

.. code-block:: php

    <?php
    $authorName = "William Shakespeare";
    function setAuthorName()
    {
        Global $authorName;
        $authorName = "Charles Dickens";
    }
    setAuthorName();
    echo $authorName;
    //output: Charles Dickens
    ?>
