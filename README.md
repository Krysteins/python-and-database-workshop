# Python and database workshop

# create_db.py
Python script: create_db.py, in which:<br />
- Create a database. If the database already exists, the script should inform the user about it without interrupting its operation.
- Create a table holding the users' data. It should have the following columns:
  - id - primary key (preferably serial type),
  - username - string (varchar (255)),
  - hashed_password - string (varchar (80)). If such a table already exists, the script inform the user about it without interrupting its execution.
- Create a table that stores messages. It has the following columns:
  - id - primary key (preferably serial type),
  - from_id - foreign key to the users table,
  - to_id - foreign key to the users table,
  - creation_date - timestamp, added automatically,
  - text - string (varchar (255)). If such a table already exists, the script inform the user about it without interrupting its execution.

# models.py 
There is code in this model with classes that handle each table.<br />

## User class
1. The class serving the user. It has the following attributes:
   - _id - set to -1 when created,
   - username - username,
   - _hashed_password - hashed user password.
2. Provides _id and _hashed_password readable externally.
3. Add a method that will allow to set a new password.
4. Add methods to handle the database:
   - save_to_db - save to the database or update the object in the database,
   - load_user_by_username - load the user from the database based on his name, 
   - load_user_by_id - load the user from the database based on his id, 
   - load_all_users - load all users from the database , 
   - delete - remove a user from the database and set his _id to -1.

## Message class
1. The class that will handle our messages. It has the following attributes:
   - _id - set to -1 when created,
   - from_id - sender's id, set when creating the object,
   - to_id - recipient id, set when creating the object,
   - text - text to be sent,
   - creation_data - the date the message was created.
2. Share _id outside.
3. Add methods to handle the database:
   - save_to_db - save to the database or update an object in the database,
   - load_all_messages - loading all messages.

# users.py
It is an application that serves our users.<br />
It is a console application that takes arguments entered by the user.<br />

## Create a user
If, when invoking the application, the user specifies only the following parameters: `username` and `password`:
- if the user with the given name exists - report an error,
- if there is no such user:
  - if the password is at least 8 characters long, create it using the provided data,
  - if the password is too short, an appropriate message should be displayed.

## Editing the user's password
If, when invoking the application, the user specifies parameters:
- username,
- password,
- edit,
- new_pass, it:
- check if the user exists
- check if the password is correct:
   -  check if the new password (new_pass) has the required length:
     - if it is shorter than 8 characters, report it with an appropriate message,
     - if it is long enough, set a new password,
   - if the password is incorrect, report it with an appropriate message.

## User deletion
If, when invoking the application, the user specifies parameters:
- username,
- password,
- delete, check the correctness of the password:
   - if correct - remove the user from the database,
   - if incorrect - inform the user about it with an appropriate message, eg "Incorrect Password !.

## Listing users
If the user specifies the `-l` `(--list)` parameter when invoking the application, a list of all users should be listed.

## Help
If the user specifies a different set of parameters, the help panel should be displayed to him.<br />
This can be done by calling the print_help method from the parser object.

# messages.py
A console program that allows you to send and read messages.<br />
The application accepts the following arguments from the user:
- -u, --username,
- -p, --password,
- -t, --to - username to send the message to,
- -s, --send - message content,
- -l, --list - request to list all user messages (flag).

## Listing messages
If, when invoking the application, the user specifies the parameters: `username` and `password` and sets the `-l` flag:

- will check if the user exists, if not display the appropriate message,
- check if the password is correct:
  - if not, display the appropriate message,
  - if so, list all messages sent to that user.

Each message contain:
- addressee,
- date of sending the message,
- Message content.

## Send the message

If, when launching the application, the user specifies the following parameters: `username` and` password` and additionally
will set the parameter `-t` (` --to`) and `-s` (` --send`):
- if the user exists, if not display the appropriate message,
- if the password is correct:
     - if not, display the appropriate message,
     - if so:
         - if the recipient of the message exists (`--to`), if not, inform the user about it,
         - if the message is shorter than 255 characters:
             - if not, display the appropriate message,
             - if so, compose a message and save it to the database.

## Help

If the user specifies a different set of parameters, the help panel should be displayed to him. 
This can be done by calling:
the `print_help` method from the parser object.