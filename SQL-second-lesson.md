# SQL学习---codecademy (2017.09.18)
`SQLite 是一个开源的嵌入式关系数据库`
## Second lesson
1. `查看数据表中的多个列`
```
SELECT name,imdb_rating FROM movies;
```
2. `挑选该(genre)字段的所有不同的值 distinct:不同`
```
ELECT DISTINCT genre FROM movies;
```
3. `查询movies表中的*（条件：imdb_rating字段的大于8的）显示出来`
```
SELECT * FROM movies WHERE imdb_rating > 8;
```
4. `挑选movies中的条件name为 'Se_en' 的所有信息`  `'Se_en'可以表示为Seven , Seden`
```
SELECT * FROM movies WHERE name LIKE 'Se_en';
```
5. `挑选movies中的条件name为 'a%' 的所有信息`  `'a%'可以表示为Avatar , Aliens等等`
```
SELECT * FROM movies WHERE name LIKE 'a%';
```
6. `挑选movies中的条件name为 '%man%' 的所有信息`  `'%man%'可以表示为Iron Man 2 , Pretty Woman等等`
```
SELECT * FROM movies WHERE name LIKE '%man%';
```
7. `挑选name开头从A开始但不包括J的所有信息`
```
SELECT * FROM movies WHERE name BETWEEN 'A' AND 'J';
```
8. `挑选movies中的条件year为 1990-2000 的所有信息` 
```
SELECT * FROM movies WHERE year BETWEEN 1990 AND 2000;
```
9. `挑选movies中的条件year为 1990-2000 并且genre= 'comedy'的所有信息`
```
SELECT * FROM movies WHERE year BETWEEN 1990 AND 2000 AND genre = 'comedy';
```
10. `挑选movies中的条件year < 1980 或者 genre= 'comedy'的所有信息`
```
SELECT * FROM movies WHERE genre = 'comedy' or year < 1980;
```
11. `以条件 imdb_rating 降序排序`
```
SELECT * FROM movies
ORDER BY imdb_rating DESC;

//DESC : 表示降序

ORDER BY is a clause that indicates you want to sort the result set by a particular column either alphabetically or numerically.

DESC is a keyword in SQL that is used with ORDER BY to sort the results in descending order (high to low or Z-A). Here, it sorts all of the movies from highest to lowest by their IMDb rating.
```
12. `只显示三个imdb_rating且为升序排序`
```
SELECT * FROM movies
ORDER BY imdb_rating ASC
LIMIT 3;

//retrieve 取回
```
13. 
```
SELECT is the clause you use every time you want to query information from a database.
WHERE is a popular command that lets you filter the results of the query based on conditions that you specify.
LIKE and BETWEEN are special operators that can be used in a WHERE clause
AND and OR are special operators that you can use with WHERE to filter the query on two or more conditions.
ORDER BY lets you sort the results of the query in either ascending or descending order.
LIMIT lets you specify the maximum number of rows that the query will return. This is especially important in large tables that have thousands or even millions of rows.
```
