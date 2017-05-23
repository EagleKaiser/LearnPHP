Classess & Objects
==================

Creating a Classess
-------------------

.. code-block:: php

    <?php
    class Person
    {
    }

Creating an Object
------------------

.. code-block:: php

    <?php
    class Person
    {
    }
    $myObject = new Person();
    ?>

Create Properties
-----------------

.. code-block:: php

    <?php
    class Person
    {
        public $firstName = "Samel";
        public $lastName = "Clemens";
        public $yearBorn = "1988";
    }
    $myObject = new Person();
    ?>

Accessing Properties
--------------------

.. code-block:: php

    <?php
    class Person
    {
        public $firstName = "Samel";
        public $lastName = "Clemens";
        public $yearBorn = "1988";
    }
    $myObject = new Person();
    echo $myObject->firstName."<br>";
    $myObject->firstName = "S.L";
    echo $myObject->firstName;
    //output:
    //Samel
    //S.L
    ?>

.. note:: 

    we don't use $ to access the properties values

Creating Constans
-----------------

.. code-block:: php

    <?php
    class Person
    {
        const AVG_LIFE_SPAN = 79;
        public $firstName = "Samel";
        public $lastName = "Clemens";
        public $yearBorn = "1988";
    }
    $myObject = new Person();
    echo $myObject::AVG_LIFE_SPAN."<br>";
    echo Person::AVG_LIFE_SPAN;
    //output
    //79
    //79
    ?>

.. note:: 

    we can access constant value by using the object of the class or the class itself

Creating Methods
----------------

.. code-block:: php

    <?php
     class Person
    {
        const AVG_LIFE_SPAN = 79;
        public $firstName;
        public $lastNamens;
        public $yearBorn;

        function __construct()
        {
            echo "I'm in the constructor";
            $this->firstName = "Samel";
            $this->lastName = "Clemens";
            $this->yearBorn = "1988";
        }

        public function getFirstName()
        {
            return $this->firstName;
        }
        public function setFirstName($tempName)
        {
            $this->firstName = $tempName;
        }
    }
    $myObject = new Person();
    echo $myObject->getFirstName()."<br>";
    echo $myObject->getFirstName()."<br>";
    $myObject->setFirstName("Sam");
    echo $myObject->getFirstName();
    //I'm in the constructorSamel
    //Samel
    //Sam
    ?>

.. note:: 

    * A constructor will execute when creating a new object
    * A conststructor is created by using function __construct(){}

Initial Parameters
------------------

.. code-block:: php

    <?php
   
     class Person
    {
        const AVG_LIFE_SPAN = 79;
        public $firstName;
        public $lastNamens;
        public $yearBorn;
        function __construct($tempFirst = "", $tempLast = "", $tempBorn = "")
        {
            $this->firstName = $tempFirst;
            $this->lastName = $tempLast;
            $this->yearBorn = $tempBorn;
        }
        public function getFirstName()
        {
            return $this->firstName;
        }
        public function setFirstName($tempName)
        {
            $this->firstName = $tempName;
        }
    }
    $myObject = new Person("Samuel Langhorne", "Clemens", 1899);
    echo $myObject->getFirstName();
    //output:
    //Samuel Langhorne
    ?>

.. note:: 

    Initializing parameters of the constructor prevent an error from happinnig if no parameters were givin

Inheritance
-----------

.. code-block:: php

    <?php
     class Person
    {
        const AVG_LIFE_SPAN = 79;
        public $firstName;
        public $lastNamens;
        public $yearBorn;
        function __construct($tempFirst = "", $tempLast = "", $tempBorn = "")
        {
            echo "Person Constructor<br>";
            $this->firstName = $tempFirst;
            $this->lastName = $tempLast;
            $this->yearBorn = $tempBorn;
        }
        public function getFirstName()
        {
            return $this->firstName;
        }
        public function setFirstName($tempName)
        {
            $this->firstName = $tempName;
        }
        public function getFullName()
        {
            echo "Person->getFullName()<br>";
            return $this->firstName." ".$this->lastName."<br>";
        }
    }
    class Author extends Person
    {
        public $penName = "Mark Twain";
        public function getPenName()
        {
            return $this->penName."<br>";
        }
        //child methods with same name will overide parents method
        public function getFullName()
        {
            echo "Author->getFullName()<br>";
            //firstName and lastName are parents attriputes that child can access
            return $this->firstName." ".$this->lastName."<br>";
        }
    }
    //Author will access parent method getFullName()
    $newAuthor = new Author("Samuel Langhorne", "Clemns", 1899);
    echo $newAuthor->getFullName();
    echo $newAuthor->getPenName();
    //output
    //Person Constructor
    //Author->getFullName()
    //Samuel Langhorne Clemns
    //Mark Twain
    ?>

.. note:: 

    If we comment child function getFullName() output will be Person->getFullName()

Public, Protected and private
-----------------------------
`php cocumentation for visibility <http://www.php.net/manual/en/language.oop5.visibility.php>`_ 

.. code-block:: php

    <?php
    /**
     * Define MyClass
     */
    class MyClass
    {
        public $public = 'Public';
        protected $protected = 'Protected';
        private $private = 'Private';

        function printHello()
        {
            echo $this->public;
            echo $this->protected;
            echo $this->private;
        }
    }

    $obj = new MyClass();
    echo $obj->public; // Works
    echo $obj->protected; // Fatal Error
    echo $obj->private; // Fatal Error
    $obj->printHello(); // Shows Public, Protected and Private


    /**
     * Define MyClass2
     */
    class MyClass2 extends MyClass
    {
        // We can redeclare the public and protected properties, but not private
        public $public = 'Public2';
        protected $protected = 'Protected2';

        function printHello()
        {
            echo $this->public;
            echo $this->protected;
            echo $this->private;
        }
    }

    $obj2 = new MyClass2();
    echo $obj2->public; // Works
    echo $obj2->protected; // Fatal Error
    echo $obj2->private; // Undefined
    $obj2->printHello(); // Shows Public2, Protected2, Undefined

    ?> 

.. note:: 

    * public scope to make that variable/function available from anywhere, other classes and instances of the object
    * protected scope when you want to make your variable/function visible in all classes that extend current class including the parent class
    * private scope when you want your variable/function to be visible in its own class only

example


.. code-block:: php

    <?php   
     class Person
    {
        const AVG_LIFE_SPAN = 79;
        protected $firstName;
        protected $lastNamens;
        protected $yearBorn;
        function __construct($tempFirst = "", $tempLast = "", $tempBorn = "")
        {
            echo "Person Constructor<br>";
            $this->firstName = $tempFirst;
            $this->lastName = $tempLast;
            $this->yearBorn = $tempBorn;
        }
        protected function getFirstName()
        {
            return $this->firstName;
        }
        protected function setFirstName($tempName)
        {
            $this->firstName = $tempName;
        }
        protected function getFullName()
        {
            echo "Person->getFullName()<br>";
            return $this->firstName." ".$this->lastName."<br>";
        }
    }
    class Author extends Person
    {
        protected $penName = "Mark Twain";
        public function getPenName()
        {
            return $this->penName."<br>";
        }
        public function getFullName()
        {
            echo "Author->getCompleteName()<br>";
            //access protected properties through this public method
            return $this->firstName." ".$this->lastName."a.k.a. ".$this->penName."<br>";
        }
    }
    $newAuthor = new Author("Samuel Langhorne", "Clemns", 1899);
    echo $newAuthor->getFullName();
    //output
    //Person Constructor
    //Author->getCompleteNme()
    //Samuel Langhorne Clemnsa.k.a. Mark Twain    
    ?>

Static
------

.. code-block:: php

    <?php
    class Foo
    {
        public static $centuryPopular = "19th";
        public static function getCentury()
        {
            return self::$centuryPopular;
        }
    }
    echo Foo::$centuryPopular;
    echo "<br>";
    echo Foo::getCentury();
    ?>

.. note:: 

    * Use self to access static properties inside a class
    * Use parent to access properties from an ingerited class

Include and Require
-------------------

.. code-block:: php

    <?php
    include 'Person.php';
    include_once 'Authors.php';
    require 'RandomClass.php';
    $newAuthor = new Author("sam", "clem", 1889);
    echo $newAuthor->getCompleteName();
    ?>

.. note:: 

    * If class does not exist include will continue to run the rest of the script while requre will terminate when it cannot find the necessary file 
