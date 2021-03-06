GetUser Method
==============

Returns user account data for a single user.

Request Format
--------------

+-----------------+----------------------------+--------+-------------+
| *Parameter*     | *Description*              | *Type* | *Required*  | 
+=================+============================+========+=============+
| `RequestMethod` | GetUser                    | String | Yes         | 
+-----------------+----------------------------+--------+-------------+
| `UserID`        | UUID of the user           | UUID   | Optional^1^ | 
+-----------------+----------------------------+--------+-------------+
| `Name`          | Name of the user           | String | Optional^1^ |
+-----------------+----------------------------+--------+-------------+
| `Email`         | E-mail address of the user | String | Optional^1^ |
+-----------------+----------------------------+--------+-------------+

  * ^1^At least one search parameter must be given
  * If a `UserID` of "0000000-0000-0000-0000-000000000000" is given, the user with the highest `AccessLevel` is returned

Sample request: ::

    RequestMethod=GetUser
    &Name=John+Doe


Response Format
---------------

+-------------+----------------------------------------------+---------+
| *Parameter* | *Description*                                | *Type*  |
+=============+==============================================+=========+
| `Success`   | True if a user object was returned, False if | Boolean |
|             | a Message was returned                       |         |
+-------------+----------------------------------------------+---------+
| `User`      | User object, see below                       | `*`     |
+-------------+----------------------------------------------+---------+
| `Message`   | Error message                                | String  |
+-------------+----------------------------------------------+---------+


User Object
-----------

+---------------------+--------------------------------------------+---------+
| *Parameter*         | *Description*                              | *Type*  |
+---------------------+--------------------------------------------+---------+
| `UserID`            | UUID for the user account                  | UUID    |
+---------------------+--------------------------------------------+---------+
| `Name`              | Account name                               | String  |
+---------------------+--------------------------------------------+---------+
| `Email`             | Account e-mail address                     | String  |
+---------------------+--------------------------------------------+---------+
| `AccessLevel`       | 0-255 value indicating the access level of | Integer |
|                     | this user. Described in more detail on the |         |
|                     | AccessLevel page                           |         |
+---------------------+--------------------------------------------+---------+
| *`Variable Fields`* | Free form key value pairs. See AddUserData | `*`     |
|                     | for a list of common user data fields      |         |
+---------------------+--------------------------------------------+---------+

Success: ::

    {
        "Success":true,
        "User":
        {
            "UserID":"efb00dbb-d4ab-46dc-aebc-4ba83288c3c0",
            "Name":"John Doe",
            "Email":"john.doe@email.com",
            "AccessLevel":0,
            "CreationDate":"1261042614",
            "LastLoginDate":"1264728529",
            "HomeLocation":"http://examplegrid.com/scenes/Homeland/128/128/25",
            "LastLocation":"http://examplegrid.com/scenes/BraveNewWorld/53/97/23"
        }
    }


Failure: ::

    {
        "Success":false,
        "Message":"User does not exist"
    }

