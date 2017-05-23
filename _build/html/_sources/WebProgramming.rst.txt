Web Programming
===============

Setup web site location in Linux
--------------------------------

* Linux store web applications in /var/www/html
* There are two options one is to move the files to the location /var/www/html or we can create a symLink in the same directory that point to any file location
* To create symLink use the following command
.. code-block:: console

    sudo ln -s /home/projectName/web/ /var/www/html/symLinkName
    //ln-> link, -s symbolic, project location, symLink location
    //symLinkName will be used with localhost/symLink
    //to view symLink of a folder type the following:
    ls -al /var/www/hml/

* Customize netbeans to run project as local web site from Customize->run configuration
* And change project url to be http://localhost/symLinkName

Setup web site location in windows
----------------------------------

* XAMPP store web applications in c:\xampp\htdocs
* Customize netbeans to run project as local web site from Customize->run configuration
* In windows IIS is running in port 80 so from XAMPP menu go to config and search for the number 80 and change it to 81
* Customize netbeans project url to http://localhost:81/PHPFundamentals/

Sample project
--------------

* Sample project include three files: index.php, final.php, asset(folder)->styles.css with one picture

index.php
~~~~~~~~~

.. code-block:: html

    <!DOCTYPE html>
    <html>
        <head>
            <title>PHP Fundamentals</title>
            <link href="assets/styles.css" rel="stylesheet" type="text/css" />
        </head>
        <body>
            <div id="Header">
                <img src="assets/Dickens_Gurney_head.jpg" border="0" alt="">
                <h2>
                    Join Our Literature Mailing List
                </h2>
            </div>        
            <div id="Body">
                <form method="get" action="final.php" >
                    <div>
                        <label>Favorite Author:</label>
                        <select name="author">
                            <option></option>
                        </select>
                    </div>		
                    <div class="multiple">
                        <label>Favorite Century:</label>
                        17th Century <input type="checkbox" name="century[]" value="17th">
                        18th Century <input type="checkbox" name="century[]" value="18th"> 
                        19th Century <input type="checkbox" name="century[]" value="19th"> 
                    </div>
                    <div>
                        <label>Comments:</label>
                        <textarea name="comments"></textarea>
                    </div>
                    <div>
                        <label>Name:</label>
                        <input type="text" name="name" />
                    </div>
                    <div>
                        <label>E-mail Address:</label>
                        <input type="text" name="email" />
                    </div>
                    <div  class="multiple">
                        <label>Receive Newsletter:</label>
                        Yes <input type="radio" name="newsletter" value="no">
                        No <input type="radio" name="newsletter" value="yes">
                    </div>
                    <div class="multiple">
                        <label>&nbsp;</label>
                        <input type="submit" name="submit" value="Join Mailing List">
                    </div>
                </form>
            </div>
        </body>
    </html>

.. note:: 

    add [] to checkbox names to accept multible input values or it will take the first only

final.php
~~~~~~~~~

.. code-block:: html

    <!DOCTYPE html>
    <html>
        <head>
            <title>PHP Fundamentals</title>
            <link href="assets/styles.css" rel="stylesheet" type="text/css" />
        </head>
        <body>
            <div id="Header">
                <img src="assets/Dickens_Gurney_head.jpg" border="0" alt="">
                <h2>
                    Mailing List Information
                </h2>
            </div>        
            <div id="Body">
                <div>
                    <label>Favorite Author:</label> 
                    <span> </span>
                </div>		
                <div>
                    <label>Favorite Century:</label>
                    <span> </span>
                </div>
                <div>
                    <label>Comments:</label>
                    <span> </span>
                </div>
                <div>
                    <label>Name:</label>
                    <span> </span>
                </div>
                <div>
                    <label>E-mail Address:</label>
                    <span> </span>
                </div>
                <div>
                    <label>Receive Newsletter:</label>
                    <span> </span>
                </div>
            </div>
        </body>
    </html>

styles.css
~~~~~~~~~~

.. code-block:: css

    * { padding: 0; margin: 0; font-family: sans-serif;  font-size: 18px;  color: #f9f9f9; background: #888; -webkit-box-sizing: border-box;    -moz-box-sizing: border-box; box-sizing: border-box;}
    h2 { text-align: center; font-size: 30px;  padding-top: 50px;  }
    body { padding-top: 20px; }
    div { margin: 0 0 20px 0; }
    label { float: left; display: block; width: 200px; text-align: right; padding-right: 20px; }
    input, textarea, select { width: 400px; border: solid 3px #555; padding: 5px; background: #F9F9F9; color: #555; }
    input[type=submit] { background: #555; border: solid 5px #333; color: #F9F9F9; padding: 5px;  }
    img { height: 150px; float: left; }

    #Body { width: 700px; margin: 0 auto; }
    #Header { text-align: center; padding: 0 0 20px 0; width: 500px; overflow: hidden; margin: 0 auto;   }
    .multiple input { width: auto; margin: 0 15px 0 5px; }
    .multiple { font-size: 14px; }

Connect Website to database
---------------------------

* Create a new php file in the asset folder called dbinfo.php

.. code-block:: php

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

    //don't use $connection->close();
    ?>

* At the beggining of index.php add the following code
.. code-block:: php

    <?php
    require 'assets/dbinfo.php';

    $query = "SELECT id, first_name, last_name, pen_name FROM Authors ORDER BY first_name";
    $resultObj = $connection->query($query);
    ?>

Create dropdown List
--------------------

* In index.php create an author dropdown List

.. code-block:: php

    <select name="author">
        <?php while($row = $resultObj->fetch_assoc()): ?>
            <option value="<?=$row['id']?>"><?=$row['first_name']?> <?=$row['last_name']?></option>
        <?php endWhile; ?>
    </select>

.. note:: 

    * id is inside the option tag and it will be displayed in the source code of the page
    * Type a space between first_name and last_name
 
$_GET
-----

* get will diaplay the suppmeted values from the form in the url, which is insecure
* $_GET is a predefined variable that stores the get values in an associated array
* To get the valus of $_GET use the following code in the top of final.php

.. code-block:: php

    <?php
    echo "<pre>";
    print_r($_GET); //will print all element in the array
    echo "<pre>";

    echo $_GET['author']; //will print specific element from the array
    ?>    

.. note:: 

    * To see the results open index and supmet values which will redirect to final.php
    * echo "<pre>"; will format $_GET array values in a readable format
    
$_POST
------

* post will not diaplay the supmetted values from the form in the url, which is secure
* $_POST is a predefined variable that stores the post values in an associated array
* To get the valus of $_GET use the following code in the top of final.php

.. code-block:: php

    <?php
    echo "<pre>";
    print_r($_POST); // will print all element in the array
    echo "<pre>";
    echo $_POST['author'];
    ?>

* after examinning the result remove the previous code and change all get to post in the project
* Now modify final.php with the following code

.. code-block:: php

    <div id="Body">
            <div>
                <label>Favorite Author:</label> 
                <span><?=$_POST['author']?></span>
            </div>		
            <div>
                <label>Favorite Century:</label>
                <span><?=$_POST['century']?></span>
            </div>
            <div>
                <label>Comments:</label>
                <span><?=$_POST['comments']?></span>
            </div>
            <div>
                <label>Name:</label>
                <span><?=$_POST['name']?></span>
            </div>
            <div>
                <label>E-mail Address:</label>
                <span><?=$_POST['email']?></span>
            </div>
            <div>
                <label>Receive Newsletter:</label>
                <span><?=$_POST['newsletter']?></span>
            </div>
        </div>

Form Validation
---------------

* To create a validation to a form first change the action of the form to redirect to the same page (index->index)
* Add the following code to the top of the index file

.. code-block:: php

    <? php
    if(count($_POST) > 0) // this will not allow the validation to be triggered when loading the page for the first time
    {
        if(!empty($_POST['email']))
        {
            header('Location: final.php');
        }
        else
        {
            $emailError = 'validation';
        }
    }
    ?>

.. note:: 

    * Add "validation" as a class in the style.css file with the following code
    .. code-block:: css
    
        .validation label { color: #CC0000; }
        .validation input { border-color: #CC0000; }

    * Add this class to validate email input <div class="<?=$emailError?>"> that should not be embty
    * If posting to the same page $_POST will not take the values to a redirected page like final.php
    * Implement session to take the values to a redirected page

session_start()
---------------

* Add include.php file in the assets folder, this file will hold all required codes by other pages to prevent changing the same codes in multible pages
* Include the include.php file in the index.php and final.php pages by using the following code
.. code-block:: php

    <?php
    include 'assets/include.php';
    ?>


.. note:: 

    * Sessions will preserve data and allow it to be accessed through the enrire Website
    * To start a session use the method session_start() in the pages that need to access the data

$_SESSION
---------

* $_SESSION is an associated array that can be used to store data to be accessed throughout the web pages
* Modify index.php with the following code

.. code-block:: php

    <?php
    if(count($_POST) > 0)
    {
        if(!empty($_POST['email']))
        {
                //$_SESSION['formWasPosted'] = 'yes';
                $_SESSION['formPostData'] = $_POST; //This will store $_POST values to $_SESSION
                header('Location: final.php');
        }
        else
        {
                    $emailError = 'validation';
        }
    }
    ?>

* To see $_SESSION values add the following code to the top of final.php

.. code-block:: php

    <?php
    include 'assets/include.php';

    echo "<pre>";
    print_r($_SESSION);
    echo "<pre>";
    ?>

* Now after supmetting the index form the values of $_SESSION will be displayed
* Modify final.php to have the following code

.. code-block:: php

    <?php
    include 'assets/include.php';

    $postedData = $_SESSION['formPostData'];
    ?>
    <!DOCTYPE html>
    <html>
        <head>
            <title>PHP Fundamentals</title>
            <link href="assets/styles.css" rel="stylesheet" type="text/css" />
        </head>
        <body>
            <div id="Header">
                <img src="assets/Dickens_Gurney_head.jpg" border="0" alt="">
                <h2>
                    Mailing List Information
                </h2>
            </div>        
            <div id="Body">
                <div>
                    <label>Favorite Author:</label> 
                    <span><?=$postedData['author']?></span>
                </div>		
                <div>
                    <label>Favorite Century:</label>
                    <span><?=$postedData['century']?></span>
                </div>
                <div>
                    <label>Comments:</label>
                    <span><?=$postedData['comments']?></span>
                </div>
                <div>
                    <label>Name:</label>
                    <span><?=$postedData['name']?></span>
                </div>
                <div>
                    <label>E-mail Address:</label>
                    <span><?=$postedData['email']?></span>
                </div>
                <div>
                    <label>Receive Newsletter:</label>
                    <span><?=$postedData['newsletter']?></span>
                </div>
            </div>
        </body>
    </html>

* The $postedData variable will hold the associated array $_SESSION which in turn holds $_POST data from the index form
* If session is not distroyed it will hold data even if returened to thu supmet page afterword

session_desroy()
----------------

* Modify final.php with the following code at the top

.. code-block:: php

    <?php
    include 'assets/include.php';
    if(isset($_SESSION['formPostData'])) //If there is a session comming from index.php
    {
        $postedData = $_SESSION['formPostData'];
        unset($_SESSION['formPostData']); // this will empty the session after using it
    }
    else {
        header('Location: index.php'); // If there is no session, will be redirected to index.php
    }
    ?>



