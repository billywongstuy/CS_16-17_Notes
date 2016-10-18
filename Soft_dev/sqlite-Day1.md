##Aim: [data] based LIFE


WHAT IS DESIRED FOR INFO STORAGE AND ACCESS?
  -No CSV
  -O(1) search
  -managed concurrency
  -# of fields per user  - order history


Students                           

| Name      | Id    |              
| --------- | -----:|              
| a         | 0     |              
| b         | 1     |              
| c         | 2     |              


Courses

| Name      | Id   | Mark   |
| --------  |:----:| ------:|
| SoftDev   | 0    | 80     |
| SoftDev   | 1    | 55     |
| SoftDev   | 2    | 45     |
| Systems   | 2    | 90     |



relational database

SQLite  ($sqlite3    exit with Crtl+D or .quit)

Row in a table is called a record
inser: when you add a row to a table

```sql
$sqlite3 foo.db
>create table
     >students(name TEXT, id INTEGER);
     >insert into students value ("Bob,777);
```

--------

create table: add a table to a data base
  -create table <name> (<column name> <data type>, ...);

TEXT, INTEGER, REAL, NUMERIC (can be floating point), BLOB

insert into: insert a record into a table
  -insert into <tbl_name> values ( <field 1>, <field 2>, ...);

select * from <tbl_name> : show all entries in table <tbl_name>
  -(* for all, or use a value)


.tables : to see tables in .db file
