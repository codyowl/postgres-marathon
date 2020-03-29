# postgres-marathon
An insanely pretty cheat sheet for postgres !


## Commands:

	\l    : list out database
	\c    : connect to a database
	\d    : describe all the table
	\d <table_name> : description about a single table
	\dt   : list out all the tables
	\i <sqlfilepath/sqlfile.sql> : to dump a sql file to postgres


## create and delete queries:

	-	Create a database:

		CREATE DATABASE <database_name>;

	-	Create a table:

		CREATE TABLE <table_name> (<column_name1> datatype(size), <column_name2> datatype(size));

		list of datatypes:

			<NEEDTOFILL>

		list of constraints:
		
			BIGSERIAL			:	Used to refer a field as autoincremental one
			NOT NULL			:
			NULL				:
			PRIMARY KEY         :
			<NEEDTOFILL>	

	-	Deleting a database:

		DROP DATABASE <database_name>

	-	Deleting a table:

		DROP TABLE <table_name>


## Insert queries:

	- Inserting a row:

		INSERT INTO <table_name> (<column_name1>, <column_name2>) values ("value1", "value2");

## Select queries:

	- Selecting all the records from a table:

		SELECT * FROM <table_name>;

	- Selecting particular column from a table:
	
		SELECT <column_name> FROM <table_name>;			

	- Selecting multiple columns from a table:

		SELECT <column_name1>, <column_name2> FROM <table_name>;

	-	WHERE CLAUSE AND:

		- WHERE:

			SELECT * FROM <table_name> WHERE <condition>;

		- AND:

			SELECT * FROM <table_name> WHERE <condition1> AND <condition2>;

		- AND & OR:

			SELECT * FROM <table_name> WHERE <condition1> AND (<sub_condition1> OR <sub_condition2>)


	- IN:

		SELECT * FROM <table_name> WHERE <column_name1> IN ("value1", "value2", "value3")

	- BETWEEN:

		SELECT * FROM <table_name> WHERE <column_name1> BETWEEN <data_type>(if date) 'value1' AND 'value2'

	- LIKE:

		SELECT * FROM <table_name> <column_name> LIKE '%.com' (Will retrieve all the resuls that ends with ".com" as its string)

		Using "_" to count the words:

			SELECT * FROM <table_name> WHERE <column_name> LIKE '____@%' (Will retrieve 4 letter words since 4 underscores are used) 

		Finding rows with a Starting letter (ex: P):
		
			SELECT * FROM <table_name> WHERE <column_name> LIKE 'p%';

## Sorting rows:

	- Sorting rows in ascending/descending order: (ORDER BY)

		- sort out rows in ascending order:

			SELECT * FROM <table_name> ORDER BY <column_name> (if the columns is a string then it will sortout in alphabetical order)

		- sort out rows in descending order:

			SELECT * FROM <table_name> ORDER BY <column_name> DESC (adding "DESC" will sort out in descending order)

		- Sorting based on multiple column names:

			SELECT * FROM <table_name> ORDER BY <column_name1>, <column_name2>

	- Finding datas without duplication: (DISTINCT)

		SELECT DISTINCT <column_name> ORDER BY <column_name>;	



## Comparison operators:

	- Typical mathematical comparison operators:

		"<", ">", ">=", "<=", "<>"(not equalto)

## limiting query results:

	- Limiting query results using LIMIT:

		SELECT * FROM <table_name> LIMIT 5; (The result will display first five records)

	- limiting query results using OFFSET:
	
		SELECT * FROM <table_name> OFFSET 5; (The result will displayed by excluding the first five records)

	- fetch:

		SELECT * FROM <table_name> OFFSET 5 FETCH FIRST 5 ROW ONLY; (NEEDTOFILLUP)	

## Grouping query results:

	<NEEDTOFILLUP>

	GROUP BY:

		SELECT <column_name> COUNT(*) FROM GROUP BY <column_name>;

	GROUP BY HAVING:
	
		SELECT <column_name> COUNT(*) FROM GROUP BY <column_name> HAVING COUNT(*) > 10;	 

## Aggregate functions :

	COUNT:

		SELECT COUNT (<column_name>) FROM <table_name>;

	MAX:

		SELECT MAX (<column_name>) FROM <table_name>;

	MIN:

		SELECT MIN (<column_name>) FROM <table_name>;

	AVG:

		SELECT AVG (<column_name>) FROM <table_name>;

		SELECT ROUND (AVG (<column_name>)) FROM <table_name>; (rounding the avg value)

	SUM:

		SELECT SUM(<column_name>) FROM <table_name>;