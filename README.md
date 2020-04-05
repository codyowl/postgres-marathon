# postgres-marathon
An insanely pretty cheat sheet for postgres !


## Commands:

	\l    : list out database
	\c    : connect to a database
	\d    : describe all the table
	\d <table_name> : description about a single table
	\dt   : list out all the tables
	\i <sqlfilepath/sqlfile.sql> : to dump a sql file to postgres
	\x : will display the result in expanded way


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

## Update queries :

	- Updating a row :

		UPDATE <table_name> SET <column_name> = 'value' WHERE <condition>;

	- Updating multiple column name's values
	
		UPDATE <table_name> SET <column_name_1> = 'value 1', <column_name_2> = 'value 2' WHERE <condition>;			

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

## COALESCE :

	Will return a default value for a column if it is supposed to by a null value

	SELECT COALESCE(<column_name>, "string to return when its null") FROM <table_name>

## NULLIF :
 
    Will return null if the given two arguments are equal instead of throwing an error.

## DATE & TIMESTAMP :

	NOW :

		Will return current date, month and year along with time

		SELECT NOW()

	DATE :
	
		Function used to get date along from NOW() function.

		SELECT NOW()::DATE;

	TIME :
	
		Function used to get current time from NOW() function.

		SELECT NOW()::TIME;

	Manipulating date to substract and add data:
	
		INTERVAL YEARS:

			SELECT NOW() - INTERVAL '<number> YEARS'; 	

			SELECT NOW() + INTERVAL '<number> YEARS';	

			EX : SELECT NOW () - INTERVAL '10 YEARS' => Will minus 10 years from now and return it 	    			

		INTERVAL MONTHS:

			SELECT NOW() - INTERVAL '<number> MONTHS';

			SELECT NOW() + INTERVAL '<number> MONTHS';

		INTERVAL DAYS:

			SELECT NOW() - INTERVAL '<number> DAYS';

			SELECT NOW() + INTERVAL '<number> DAYS';

		Getting date alone :
		
			SELECT NOW()::DATE + INTERVAL '10 MONTHS';	

	Extracting individual data from a timestamp:

		EXTRACT YEAR:

			SELECT EXTRACT(YEAR FROM NOW()); => return year alone from NOW()

		EXTRACT MONTH:
		
			SELECT EXTRACT(YEAR FROM NOW()); => return month alone from NOW()

		EXTRACT DAY:
		
			SELECT EXTRACT(YEAR FROM NOW()); => return day alone from NOW()		 		


## Constraints :

	PRIMARY KEY CONSTRAINT:

		Defining primary key while creating a table:

			CREATE TABLE <table_name> ( <column_name> NOT NULL PRIMARY KEY);

		Dropping primary key:
		
			ALTER TABLE <table_name> DROP CONSTRAINT <primary_key_index_name> => \d <table_name> will return the primary key constraint name	

		Adding primary key:

			ALTER TABLE <table_name> ADD PRIMARY KEY <column_name>; => Adding a primary key to a column name is possible only if it contains unique value in populated data in a table

	UNIQUE CONSTRAINT:

		Adding unique constraint with constraint name:

			ALTER TABLE <table_name> ADD CONSTRAINT <unique_constraint_name> UNIQUE(<column_name>); 

			NOTE : Adding a unique key constraint is possible only if the table contains unique populated data

		Dropping unique key:
		
			ALTER TABLE <table_name> DROP CONSTRAINT <unique_key_constraint_name> 

			NOTE: \dt will return the unique key constraint name	

		Adding unique key constrain without constrain name:
		
			ALTER TABLE <table_name> ADD UNIQUE(<column_name>); 

			NOTE : This will create an unique key constrain by a random name which can be seen using \d	

	Things to Note:
	
		You can have n number of UNIQUE key in a table but you can have only on PRIMARY KEY		

	CHECK CONSTRAINT :	

		Used to do string based validation for a column.Ex : Allowing only male of female to a column named gender.

		Adding CHECK constraint:

			ALTER TABLE <table_name> ADD CONSTRAINT <check_constraint_name> CHECK (<column_name> = 'string1' or <column_name> = 'string2') 	

			Ex :

			ALTER TABLE person ADD CONSTRAINT gender_constraint CHECK (gender='Female' OR gender='male') 

			NOTE : Adding check constrain with string validation is possible only if the populdated data contains the mentioned string or else we have to delete the particular row which doesn't contains the mentioned strings on CHECK constraint

	FOREIGN KEY:

		Defining foreign key at the time of table creation :

			CREATE TABLE <talbe_name_1> ( <column_name_1>, <column_name_2>, <foreign_key_column_name> REFERENCES <table_name_2> UNIQUE (<foreign_key_column_name>);

		Note : The table which got refered in REFERENCES should be created first.

		Deleting Foreign key rows:

			Make sure to delete the Foreign key which got refered in the row before deleting the row.

		[Diving Deep into Foreign Key](WIP) 

## ON CONFLICT :

	Exception handling, will do nothing when exceptin occurs

	<inserting_query> 
	ON CONFLICT (<column_name>) DO NOTHING

	NOTE : Having a column name as unique constraing will raise an error when we add duplicate value to it, having ON CONFLICT will simply wont do anything if it does have a duplicate value for the column name

	ON CONFLICT DO UPDATE :

	Will update things when the row exists or create a new one

	<insert query>
	ON CONFLICT DO UPDATE SET <column_name> = EXCLUDED.<column_name>


## JOINS :

	INNER JOIN :

		SELECT * FROM <table_name_1> JOIN <table_name_2> ON table_name_1.column_name = table_name_2.column_name

		Selecting multiple column name:

			SELECT table_name_1.column_name_1, table_name_2.column_name_1, table_name_2.column_name_2
			FROM <table_name_1>
			JOIN <table_name_2> ON <table_name_1>.column_name_1 = <table_name_2>.column_name_1

	LEFT JOIN :

		SELECT * FROM <table_name_1> 
		LEFT JOIN <table_name_2> ON table_name_2.column_name1 = table_name_1.column_name1

		Note : This will return all the rows joining table one and two including null values

	[DIVING DEEP INTO JOINS](WIP)

## Data extraction and importion:

	Extracting data to a csv file:

		\copy (<query>) TO 'path/to/filename.csv' DELIMITER ',' CSV HEADER;

## Extensions :

			 		

