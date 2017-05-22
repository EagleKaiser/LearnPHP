Databases
=========

Supported Databases
-------------------

* MongoDB (Document oriented database)   
* MS SQL (Microsoft SQL)
* MySQL/MariaDB
* PostgreSQL
* SQLite

PDO vs. MySQLi (Connection Methods)
-----------------------------------

+-----------------------------------------------+---------------------------------+-----------------------------------+
| PDO                                           | PDO & MySQL                     | MySQLi                            |
+===============================================+=================================+===================================+
| Supports Client-side Prepared Statemnts       | Object-oriented                 | Can use Procedural Call           |
+-----------------------------------------------+---------------------------------+-----------------------------------+
| Conncts to all the Supported Databases in PHP | Supports Charsets               | Connects to MySQL, MaxDB, MariaDB |
+-----------------------------------------------+---------------------------------+-----------------------------------+
|                                               | Multiple Statements             |                                   |
+-----------------------------------------------+---------------------------------+-----------------------------------+
|                                               | Server-side Prepared Statements |                                   |
+-----------------------------------------------+---------------------------------+-----------------------------------+
|                                               | Stored Procedures               |                                   |
+-----------------------------------------------+---------------------------------+-----------------------------------+

Setting MySQL in Linux
----------------------

.. code-block:: console

    sudo apt-get update
    mysql -V
    sudo apt-get install mysql-server
    sudo apt-get install phpmyadmin
    //select apache2
    //after installation go to localhost/phpmyadmin

Setting up MySQL in Windows
---------------------------

* Install `XAMPP <http://www.apachefriends.org>`_  Apache + MariaDB + PHP + Perl 
* Main application to choose are php, mysql and phpmyadmin
* after installation is finished change apache port number to 81 by clicking config then search for 80 and change it to 81 (there are two changes)
* Start Apache and mysql services
* In netbeans start new php project

Creating a Database and Tables
------------------------------

* To access phpmyadmin go to url localhost:81/phpmyadmin
* Create a new user by choosing user accounts-> Add user accounts, type new user name, localhost, password and grant all permisions
* Create a new database, type a name then create 
* Create a table, type a table name and choose number of columns
* For primary key choose index-> primary and A_I (auto increment)
* Create a connection object variable (Connect.php)
* If using netbeans create a new php project add port :80 to localhost project location
* change run conffiguration to be (Script (run in command line))

.. code-block:: php

    //Connect.php
    <?php
    $dbPassword = "eagle";
    $dbUserName = "kai";
    $dbServer = "localhost";
    $dbName = "PHPLearn";

    $connection = new mysqli($dbServer, $dbUserName, $dbPassword, $dbName);
    //optional parametters are port and socket number
    //print_r($connection);

    if($connection->connect_errno)
    {
        exit("Database Connection Failed. Reason: ".$connection->connect_errno);
    }

    $connection->close();

Executin a Query
----------------

* Insert data into table from phpmyadmin-> Insert

Insert, Update or DELETE
~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: php

    //Connect.php
    <?php
    $dbPassword = "eagle";
    $dbUserName = "kai";
    $dbServer = "localhost";
    $dbName = "PHPLearn";

    $connection = new mysqli($dbServer, $dbUserName, $dbPassword, $dbName);
    //optional parametters are port and socket number
    //print_r($connection);

    if($connection->connect_errno)
    {
        exit("Database Connection Failed. Reason: ".$connection->connect_errno);
    }

    //$query = "DELETE FROM Authors WHERE id = 4";
    //$query = "UPDATE Authors SET pen_name = 'L. M. Montgomery' WHERE id = 2";
    $query = "INSERT INTO Authors (first_name, last_name, pen_name) VALUES ('Arthur', 'Doyle', 'Ignatius')";
    $connection->query($query);
    //to grab newly created auto incremented id use:
    echo "Newly Created Author Id: ".$connection->insert_id;
    $connection->close();

.. note:: 

    To grab the newly created id it must be primary key & auto increment

Select Statement
~~~~~~~~~~~~~~~~

.. code-block:: php

    <?php
    $dbPassword = "eagle";
    $dbUserName = "kai";
    $dbServer = "localhost";
    $dbName = "PHPLearn";
    $connection = new mysqli($dbServer, $dbUserName, $dbPassword, $dbName);
    if($connection->connect_errno)
    {
        exit("Database Connection Failed. Reason: ".$connection->connect_errno);
    }
    $query = "SELECT first_name, last_name, pen_name FROM Authors ORDER BY first_name";
    $resObj = $connection->query($query);
    if($resObj->num_rows > 0)
    {
        while($singleRowFromQuery = $resObj->fetch_assoc())
        {
            //print_r($singleRowFromQuery);
            echo "Author: ".$singleRowFromQuery['first_name'].PHP_EOL;
        }
    }
    $resObj->close();
    $connection->close();

Prepared Statement
------------------

.. code-block:: php

    <?php
    $dbPassword = "eagle";
    $dbUserName = "kai";
    $dbServer = "localhost";
    $dbName = "PHPLearn";
    $connection = new mysqli($dbServer, $dbUserName, $dbPassword, $dbName);
    if($connection->connect_errno)
    {
        die("Database Connection Failed. Reason: ".$connection->connect_errno);
    }
    $tempFirstName = 'Lucy';
    $query = "SELECT first_name, last_name, pen_name FROM Authors WHERE first_name = ?";
    $statementObj = $connection->prepare($query);

    $statementObj->bind_param("s", $tempFirstName);
    $statementObj->execute();

    $statementObj->bind_result($firstName, $lastName, $penName);
    $statementObj->store_result();


    if($statementObj->num_rows > 0)
    {
        while($statementObj->fetch())
        {
            echo $firstName." ".$lastName." (".$penName.")".PHP_EOL;
        }
    }
    $statementObj->close();
    $connection->close();

.. note:: 

    * Prepared Statements allow for outside user input to safely be used inside a query
    * Help to prefent SQL injection attacks
    * Prepare Statement uses $connection->prepare instead of $connection->query
    * bind_param will take the place of place holder ? in the select statement
    * bind_param parametters are (type string, value to the query) where value will to to place holder and must be passes by reference, therfore mmust be a variable
    * bind_param("sdi", $stringVar, $floatVar, $intVar) means the first bind parameter is a string, the second is an is decimle and the third is an integer

PDO Example
-----------

.. code-block:: php

    <?php
    $dbPassword = "eagle";
    $dbUserName = "kai";
    $dbServer = "localhost";
    $dbName = "PHPLearn";
    $connection = new PDO('mysql:host='.$dbServer.';dbname='.$dbName, $dbUserName, $dbPassword);
    $query = "SELECT first_name, last_name, pen_name FROM Authors ORDER BY first_name";
    $resultObj = $connection->query($query);

    if($resultObj->rowCount() > 0)
    {
        foreach ($resultObj as $singleRowFromQuery) {
            echo "Author: " .$singleRowFromQuery['first_name'].PHP_EOL;
        }
    }
    $resultObj = null;
    $connection = null;

+------------------------------+--------------------------+
| MySQLi                       | PDO                      |
+==============================+==========================+
| $connection = new SQLite(... | $connection = new PDO(.. |
+------------------------------+--------------------------+
| num_rows                     | rowCount                 |
+------------------------------+--------------------------+
| while loop                   | foreach                  |
+------------------------------+--------------------------+
| $connection->close()         | $connection = null       |
+------------------------------+--------------------------+


