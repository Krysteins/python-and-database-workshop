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

