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
        public $yearBorn = "1988;
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

Protected
---------

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

.. note:: 

    * we can't access protected properties or functions, trying to will through a fatal error
    * We can access protected properties through public methods 