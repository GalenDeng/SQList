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