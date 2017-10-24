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
10. `修改字段类型的操作` 
```   
ALTER TABLE table_name ALTER COLUMN column_name new_data_type 
```
11. `删除字段的操作`
```   
ALTER TABLE table_NAME DROP COLUMN column_NAME   
```
12. `新增一个margin的字段，并设置其类型为整形，并限定其值默认为0，不为空`
```
ALTER TABLE "users"."users_ext" ADD COLUMN margin INTEGER DEFAULT 0 NOT NULL;
```
13. `创建一个新的字段，默认时间为该表刚创建的时间，之后就不修改这个时间了`
```
ALTER TABLE "ads"."incomemoney" ADD COLUMN created TIMESTAMP DEFAULT CURRENT_TIMESTAMP;
```
14. 
```
select * from users.users where username = '13542148063';
```
15. `删除这一行的数据记录`
```
delete from users.users where username = '13542148063'; 
```
16. `更新字段的值`
```
update ads.advertiser set crmuuid =  '900dbc90-36c9-4e5a-9150-17f36edf0014'   where uuid = '1c97e4e4-f1bb-11e6-a4d8-0242ac110002'
```
17. `添加注释`
```
COMMENT ON COLUMN users.users_ext.crm_total_balance IS '历史总余额';
```
18. `更新字段值`
```
UPDATE  users.users_ext  set crm_balance = 10000,crm_total_balance=10000 where uuid = 'e850d0b6-360c-45a0-8177-4074d9dc85c7';
```
19. `删除记录`
```
delete from ads.advertiser  where balance is null
```