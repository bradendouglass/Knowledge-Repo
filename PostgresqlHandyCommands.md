# PSQL Handy Commands

### CLI

* `sudo -u {postgres|$WHOAMI} createdb my_site`: create a db
* `sudo su {postgres|$WHOAMI} -c psql`: log into postgres command line with
  postgres user
* `dropdb db_name` also is a quick way to terminate a database
* `drop role name` for stuck roles or one's that are hanging around
* When connecting locally simply use: `psql -d name_of_db`

### PSQL Prompt

* `\? or \h COMMAND`: Get help
* `\l`: list all databases
* `\d`: list all tables
* `\d+tableName`: describe the table
* `CREATE USER my_user WITH PASSWORD 'password';`: Create a user with a
  specified password
* `GRANT ALL PRIVILEGES ON DATABASE my_site TO my_user;`: Give
  permissions to db
* `GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO my_user`: Give all permissions to schema
* `DROP DATABASE db_name;`: Delete a database
* `CREATE DATABASE db_name;`: Creates a new database
* `\timing`: toggle timing for queries
* `alter user username with password ‘new password’;`: change password
* `ALTER DATABASE myolddbname_here RENAME TO mynewdbname_here`: change db_name
* `\c databasename`: connect to a specific database
* `SELECT * from table`: return all rows, must first be connected
* `DELETE FROM tableName;`: wipe a table clean
* `select * from pg_stat_activity where datname='YourDatabase';` to list connections
* `SELECT relation::regclass, * FROM pg_locks WHERE NOT GRANTED;` to check all items locking the db.
* `create sequence some_table_id_seq owned by some_table.id` to create a unique id sequence
  * `alter table some_table alter column id set default nextval('some_table_id_seq')` to setup the sequence.
