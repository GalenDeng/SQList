# SQL学习---codecademy (2017.09.26)
`SQLite 是一个开源的嵌入式关系数据库`
## fourth lesson

1. `创建了两个字段 （id,name）其中id为整形，且作为一个主键，而name为字符串的类型`
```
CREATE TABLE artists(id INTEGER PRIMARY KEY, name TEXT);

Using the CREATE TABLE statement we added a PRIMARY KEY to the id column.

A primary key serves as a unique identifier for each row or record in a given table. The primary key is literally an id value for a record. We're going to use this value to connect artists to the albums they have produced.

By specifying that the id column is the PRIMARY KEY, SQL makes sure that:

None of the values in this column are NULL
Each value in this column is unique
A table can not have more than one PRIMARY KEY column.
```
2. `挑选出条件为artist_id = 3的列表出来`
```
SELECT * FROM albums WHERE artist_id = 3;

Query Results
id	name	artist_id	year
8	Bad	        3	    1987
12	Thriller	3	    1982
```
3. `主键与foreign key的关系： 两个关系表间的交流`
```
SELECT * FROM artists WHERE id = 3;
SELECT * FROM albums WHERE artist_id = 3;

Query Results
id  	name
3	    Michael Jackson
id	    name	   artist_id	year
8	    Bad	        3	        1987
12  	Thriller	3	        1982


A foreign key is a column that contains the primary key of another table in the database. We use foreign keys and primary keys to connect rows in two different tables.

One table's foreign key holds the value of another table's primary key. Unlike primary keys, foreign keys do not need to be unique and can be NULL.

Here, artist_id is a foreign key in the albums table. We can see that Michael Jackson has an id of 3 in the artists table. All of the albums by Michael Jackson also have a 3 in the artist_id column in the albums table.

This is how SQL is linking data between the two tables. The relationship between the artists table and the albums table is the id value of the artists.
```
4. `从两个表中挑选各需要的字段出来`
```
select albums.name,albums.year,artists.name FROM albums,artists;

When querying more than one table, column names need to be specified by table_name.column_name

Query Results
name	            year	name
A Hard Days Night	1964	The Beatles
A Hard Days Night	1964	Elvis Presley
```
5. `把两个不同的表的某些字段结合在一起来显示，条件为：albums.artist_id = artists.id`
```
select * FROM albums JOIN artists ON albums.artist_id = artists.id;


In SQL, joins are used to combine rows from two or more tables. The most common type of join in SQL is an inner join.

An inner join will combine rows from different tables if the join condition is true. 

SELECT * specifies the columns our result set will have.

FROM albums specifies the first table we are querying

JOIN artists ON specifies the type of join we are going to use as well as the name of the second table

albums.artist_id = artists.id is the join condition that describes how the two tables are related to each other.

result:
Query Results
id	name	                artist_id	year	id	name
1	A Hard Days Night	    1	        1964	1	The Beatles
2	Elvis Presley	        2	        1956	2	Elvis Presley
4	Yellow Submarine	    1	        1968	1	The Beatles
5	Hey Jude	            1	        1970	1	The Beatles
6	Like a Virgin	        4	        1984	4	Madonna
7	From Elvis in Memphis	2	        1969	2	Elvis Presley
```
6. `合并两个表格，但是左表格的值全填，而右表格根据条件来填，若相同则填右表格的所有字段相对应的值，若不相等，右表格的所有字段填NULL`
```
SELECT * FROM  albums LEFT JOIN artists ON albums.artist_id = artists.id;

Outer joins also combine rows from two or more tables, but unlike inner joins, they do not require the join condition to be met. Instead, every row in the left table is returned in the result set, and if the join condition is not met, then NULL values are used to fill in the columns from the right table

result:
Query Results
id	name	            artist_id	year	id	name
1	A Hard Days Night	1	        1964	1	    The Beatles
2	Elvis Presley	    2	        1956	2	    Elvis Presley
3	1989		                    2014		
4	Yellow Submarine	1	        1968	1	    The Beatles
5	Hey Jude	        1	        1970	1	    The Beatles
6	Like a Virgin	    4	        1984	4	    Madonna
```
7. `把albums.name这个字段修改为Album ，把artists.name这个字段修改为Artist`
   `并把artists这个右表加入到左表中,挑选的条件为albums.artist_id = artists.id`
   `总体的挑选条件为 albums.year > 1980`
```
confusing : 混乱的; 混淆的; 令人困惑的;

SELECT albums.name AS 'Album',albums.year,artists.name AS 'Artist' FROM albums albums  JOIN artists ON albums.artist_id = artists.id WHERE albums.year > 1980;

Query Results
Album	        year	Artist
Like a Virgin	1984	Madonna
Bad	            1987	Michael Jackson
Like a Prayer	1989	Madonna
Thriller	    1982	Michael Jackson

AS is a keyword in SQL that allows you to rename a column or table using an alias.

Here we want to rename the albums.name column as 'Album', and the artists.name column as 'Artist'.

！！It is important to note that the columns have not been renamed in either table. The aliases only appear in the result set //即select * from artists的时候看不到别名的字段，字段只会出现在结果集中
```
8. `和seventh的对比`
```
SELECT albums.name AS 'Album',albums.year,artists.name AS 'Artist' ,albums.artist_id,artists.id FROM albums albums  JOIN artists ON albums.artist_id = artists.id WHERE albums.year > 1980;

Query Results
Album	        year	Artist  	        artist_id	id
Like a Virgin	1984	Madonna	            4	        4
Bad	            1987	Michael Jackson 	3	        3
Like a Prayer	1989	Madonna	            4	        4
Thriller	    1982	Michael Jackson	    3	        3
```
9. `summarize`
```
Primary Key is a column that serves a unique identifier for row in the table. Values in this column must be unique and cannot be NULL.

Foreign Key is a column that contains the primary key to another table in the database. It is used to identify a particular row in the referenced table.

Joins are used in SQL to combine data from multiple tables.

INNER JOIN will combine rows from different tables if the join condition is true.

LEFT OUTER JOIN will return every row in the left table, and if the join condition is not met, NULL values are used to fill in the columns from the right table.

AS is a keyword in SQL that allows you to rename a column or table in the result set using an alias.
```

