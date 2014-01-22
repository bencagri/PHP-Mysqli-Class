PHP-Mysqli-Class
================

Simple Mysqli Library for PHP

    | id | user_name |    user_email    |
    ------------------------------------
    | 1  | John Doe  | john@google.com  |
    | 2  | Jen Doe   | jen@google.com   |
    | 3  | Junior Doe| junior@google.com|

#Usage
===============

This class has query,table,update,delete and insert methods to easily usage.
First we need to configure our database connection.

    require("mysqli.class.php");
    $config['db_host']      = "localhost";
    $config['db_username']  = "root";
    $config['db_password']  = "password";
    $config['db_name']      = "testdb";

    $db = new db();
    
thats it.

###Inserting Data
This method gets two parameters. 
First is "table name", second is our data in array.
@param Array Data

    $db->insert("users", 
    array("user_name" => "John Doe",
          "user_email" => "john@google.com")
          );
    

###Update
This method gets three parameters.
First is "table name", second is our data in array and third is "where situation"

    $db->update("users", 
    array("user_name" => "Jen Doe",
          "user_email" => "jen@google.com),
    array("id" = "1");
    

###Delete

    $db->delete("users",
    array("id" => "1"));
    
Important : If you dont set second param, this method drops your table!

  
###List Table
This method returns array object.

     $users =  $db->table("SELECT * FROM users);
     
     foreach($users as $user){
        echo $user->user_name;
     }
     
    
###List One Row
This method list one row by your query.

    $user = $db->row("SELECT * FROM users WHERE id=1);
    
    echo $user->user_name;
    //output
    John Doe

###Field

    $count = $db->field("SELECT COUNT(id) FROM users);
    echo $count;
    //output
    3



Easy? huh.
