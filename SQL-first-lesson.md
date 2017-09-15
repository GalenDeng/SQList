# SQL学习---codecademy (2017.09.15)
`SQLite 是一个开源的嵌入式关系数据库`
## First lesson
1. 
```
SELECT * FROM celebs;   // * 为所有列
```
2. 
```
CREATE TABLE celebs (id INTEGER,name TEXT,age INTEGER);
```
3.
```
INSERT INTO celebs (id,name,age) VALUES(1,'Justin Bieber',21);
SELECT * FROM celebs;
```
4.
```
INSERT INTO celebs (id,name,age) VALUES(2,'Beyonce Knowles',33);
INSERT inTO celebs (id,name,age) VALUES(3, 'Jeremy Lin', 26);
INSERT inTO celebs (id,name,age) VALUES(4, 'Taylor Swift', 26);
SELECT name FROM celebs;
```
5. 
```
SELECT * FROM celebs;
UPDATE celebs
SET age = 16
WHERE id = 3;
SELECT * FROM celebs;
```
6. 
```
ALTER TABLE celebs ADD COLUMN twitter_handle TEXT;
//添加新的列：twitter_handle
SELECT * FROM celebs;
```
7. 
```
//添加列的字段
ALTER TABLE celebs ADD COLUMN twitter_handle TEXT;
SELECT * FROM celebs;
```
8. 
```
// 在 id=4的twitter_handle设置@taylorswift13
UPDATE celebs                
SET twitter_handle = '@taylorswift13'
WHERE id  = 4;
SELECT * FROM celebs;
```
```
//delete这个twitter_handle的值为空的栏(is NULL)
UPDATE celebs
SET twitter_handle = '@taylorswift13'
WHERE id = 4;
DELETE FROM celebs WHERE twitter_handle IS NULL;
SELECT * FROM celebs;
```
9. 
```
CREATE TABLE creates a new table.
INSERT INTO adds a new row to a table.
SELECT queries data from a table.
UPDATE edits a row in a table.
ALTER TABLE changes an existing table.
DELETE FROM deletes rows from a table.
```