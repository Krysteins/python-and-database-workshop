# Python and database workshop

## create_db.py
Python script: create_db.py, in which:<b />
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

## models.py 
There is code in this model with classes that handle each table.<b />
### User class
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
### Message class
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

