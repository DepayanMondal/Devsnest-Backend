
# Queries
1)
CREATE USER devs WITH PASSSWORD 'password';

2)
CREATE DATABASE devs_db;

CREATE DATABASE devs_db WITH OWNER devs;

3)
GRANT ALL PRIVILEGES ON DATABASE devs_db TO devs;

4) To switch user and db:
psql -h localhost -U devs devs_db;

5)
CREATE TABLE COMPANY(
id INT PRIMARY KEY NOT NULL,
name TEXT NOT NULL,
age INT NOT NULL,
address VARCHAR(50),
salary DECIMAL
);

6)
CREATE TABLE DEPARTMENT(
id INT PRIMARY KEY NOT NULL,
dept CHAR[15] NOT NULL,
emp_id INT NOT NULL
);

7) Check schems with \dn
CREATE SCHEMA devs_schema;

8)
CREATE TABLE devs_schema.company(
id INT NOT NULL,
name VARCHAR[50] NOT NULL,
age INT,
address varchar[100],
salary DECIMAL(18,2),
PRIMARY KEY(id)
);

9)
DROP SCHEMA devs_schema CASCADE;

10)
INSERT INTO company(id, name, age, address, salary) VALUES (1,'Rick',21, 'LA', 15000);
INSERT INTO company(id, name, age, address, salary) VALUES (2,'Morty', 15, 'NYC', 25000);
INSERT INTO company(id, name, age, address, salary) VALUES (3,'Richard', 35, 'California', 35000);
INSERT INTO company(id, name, age, address, salary) VALUES (4,'Wilson', 22, 'SV', 135000.123);

11)
SELECT COUNT(*) FROM company;

12)
SELECT * FROM company WHERE name LIKE 'Ri%';
SELECT * FROM company WHERE name LIKE 'RI%';
SELECT * FROM company WHERE name ILIKE 'RI%';

13)
SELECT * FROM company WHERE age BETWEEN 15 AND 25;
SELECT * FROM company WHERE age IN(15, 21, 35, 40);

14)
UPDATE company SET salary = 21345.00 WHERE id = 2;

15)
SELECT * FROM company ORDER BY id;

16)
DELETE FROM company WHERE id = 1;


17)
CREATE TABLE customers(
cust_id INT NOT NULL,
cust_name VARCHAR(20) NOT NULL,
PRIMARY KEY(cust_id)
);

CREATE TABLE contacts(
contact_id INT NOT NULL,
cust_id INT,
contact_name VARCHAR(20) NOT NULL, 
phone VARCHAR(15), 
email VARCHAR(20), 
PRIMARY KEY(contact_id),
CONSTRAINT fk_cust 
FOREIGN KEY(cust_id) REFERENCES customers(cust_id)
ON DELETE CASCADE
);

---

# SQL 
---

IN 		- Returns true if a value matches any value in the list
BETWEEN 	- Return true if a value is between a range of values ex. BETWEEN 3 AND 5
LIKE		- Return true if a value matches a pattern ex. LIKE 'Aud%' means match string starting with 'Aud'.
ILIKE		- Same as LIKE but case insensitive pattern matching.
OFFSET 		- Skip a number of rows before returning the resultset 
LIMIT		- To constrain the number of rows returned by a query (not a SQl standard)
FETCH		- Same as LIMIT and it a SQL standard. Syntax -> FETCH {FIRST|NEXT} row_cnt {ROW|ROWS} ONLY
LEFT(s, n) 	- Extracts first n characters from s 
ALL		- We can use the word ALL to allow >= or > or < or <= to act over a list ex. on result of select subquery 

ORDER BY	- Sort thr column in ASC or DESC order
GROUP BY	- Functions such as SUM and COUNT are applied to groups of items sharing values.ex."GROUP BY continent" ,the result is only one row for each different value of continent. All the other columns must be "aggregated" by one of SUM, COUNT etc.
WHERE		- filters the rows before aggregation operation
HAVING		- filters after the agregation

------------------------------------------------------------------------------------------

Some important psql commands:

1. sudo -u <role name> psql 	--> switched to <role name> and starts psql command prompt
2. \c dbname username 		--> switch connection to new database (dbname) under a user specified by <username>
3. \l				--> list all available databases
4. \dt				--> list all tables in current database
5. \d table_name		--> describe a table
6. \dn				--> list all Schemas of current database
7. \df				--> list all functions of current database
8. \dv				--> list all Views of current database
9. \du				--> list all users and their assigned roles

10. \s				--> to display command history
11. \g				--> to execute previous command
12. \i filename			--> to execute psql commands from a file 
13. \timing			--> to turn ON/OFF query execution time:w
14. \e				--> to write command in default editor(vim/nano)
15. \q				--> to quit psql

------------------------------------------------------------------------------------------

COMMON QUERIES:

- Create new user 	--> CREATE USER username WITH PASSWORD 'password';
- Drop user		--> DROP USER IF EXISTS username;
- Create new database 	--> CREATE DATABASE db_name;
- Grant privileges	--> GRANT ALL|SELECT|UPDATE|DELETE PRIVILEGES ON DATABASE db_name TO username;
- Drop database		--> DROP DATABASE IF EXISTS db_name;
- Create schema		--> CREATE SCHEMA schema_name [CASCADE];
- Create table		--> CREATE TABLE tb_name
- Insert data		--> INSERT INTO tb_name(col1, col2,...) VALUES (val1, val2,...);
- Update Column		--> UPDATE tb_name SET col = val WHERE condition;
- Delete row		--> DELETE FROM tb_name WHERE condition;
- Delete table		--> DROP TABLE IF EXISTS tb_name;

-----------------------------------------------------------------------------------------

Evaluation order in Queries:

FROM --> WHERE --> SELECT --> ORDER BY

------------------------------------------------------------------------------------------

For creating users and db:
https://www.youtube.com/watch?v=RySuQtMiBxQ


