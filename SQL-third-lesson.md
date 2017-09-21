# SQL学习---codecademy (2017.09.21)
`SQLite 是一个开源的嵌入式关系数据库`
## third lesson

1. `计算所有的行数`
```
SELECT COUNT(*) FROM fake_apps;

COUNT() is a function that takes the name of a column as an argument and counts the number of rows where the column is not NULL. Here, we want to count every row so we pass * as an argument.
```
2. `计算条件 price = 0的行数`
```
SELECT COUNT(*) FROM fake_apps WHERE price = 0;
```
3. `挑选PRICE字段的值，统计每组不同的PRICE值的相同的次数`
```
SELECT price, COUNT(*) FROM fake_apps GROUP BY price;

Query Results
price	COUNT(*)
0.0	  73
0.99	43
1.99	42
2.99	21
3.99	9
14.99	12
```
4.  `挑选PRICE字段的值，并且downloads的字段 > 20000 ,统计每组不同的PRICE值的相同的次数`
```
SELECT price,COUNT(*) from fake_apps WHERE downloads > 20000 GROUP BY price;

Query Results
price	COUNT(*)
0.0	  26
0.99	17
1.99	18
2.99	7
3.99	5
14.99	5
```
5. `计算downloads的所有的下载次数统计值`
```
SELECT SUM(downloads) FROM fake_apps;

Query Results
SUM(downloads)
3322760
```
6. `挑选category 并统计相同的category下的downloads的所有的下载次数统计值`
```
SELECT category,SUM(downloads) FROM fake_apps GROUP BY category;

Query Results
category	SUM(downloads)
Books	            160864
Business	        178726
Catalogs	        186158
Education     	  184724
Entertainment	    95168
Finance       	  178163
Food & Drink	    90950
Games	            256083
Health & Fitness	165555
Lifestyle	        166832
Medical	          77191
Music           	59367
Navigation	      152114
News	            103259
Photo & Video	    184848
Productivity	    117811
Reference	        162032
Social Networking	126549
Sports	          176988
Travel	          242116
Utilities	        96099
Weather	          161163
```
7. `挑选downloads的最大值`
```
SELECT MAX(downloads) FROM fake_apps;xuan
```
8. `挑选不同的name、category,并且條件為選擇downloads的最大值`
```
SELECT name ,category,MAX(downloads) FROM fake_apps GROUP BY category;

Query Results
name	category	MAX(downloads)
Mathzoom	Books	  30862
subzim	Business	30269
waretam	Catalogs	31087
Solotrax	Education	28916
Fax-it	Entertainment	28699
Newlam	Finance	30605
Ladex	Food & Drink	30789
Whitetexon	Games	30959
Tamplam	Health & Fitness	31075
Fasezap	Lifestyle	30829
Fixcode	Medical	26243
opecone	Music	20967
Kinice	Navigation	22277
Voyaelectronics	News	27793
Ranit	Photo & Video	28751
Vaiatamace	Productivity	28473
Sunzoomron	Reference	28861
Greenzone	Social Networking	30986
Isis	Sports	25640
Lathouse	Travel	31090
Geotexon	Utilities	28419
Solois	Weather	27167
```
9. `挑选downloads的最小值` 
```
SELECT MIN(downloads) FROM fake_apps;

Query Results
MIN(downloads)
1387
```
10. `挑选不同的name、category,并且條件為選擇downloads的最小值` 
```
SELECT name,category,MIN(downloads) FROM fake_apps GROUP BY category;

Query Results
name	category	MIN(downloads)
Toughlab	Books	1731
yearfix	Business	4587
Anstreet	Catalogs	4937
Lamsoncode	Education	3910
lanedax	Entertainment	1673
Jaytexon	Finance	8151
Can-taxon	Food & Drink	4590
Superfan	Games	2791
kanity	Health & Fitness	2299
Quohouse	Lifestyle	4109
Latzap	Medical	1902
Zimlane	Music	1387
Zerzacom	Navigation	5541
howtam	News	1826
Doublelex	Photo & Video	5504
Hexquadline	Productivity	10212
Ittechi	Reference	3874
Roundfix	Social Networking	12734
Conebase	Sports	1923
Saltcode	Travel	2836
Bamgreen	Utilities	2212
Solodotam	Weather	7132
```
11. `求downloads的字段的平均值`
```
SELECT AVG(downloads) FROM fake_apps;
```
12. `挑选不同的price,并且条件为downloads的平均值`
```
SELECT price, AVG(downloads) FROM fake_apps GROUP BY price;

Query Results
price	AVG(downloads)
0.0	  15762.2602739726
0.99	15971.511627907
1.99	16952.5952380952
2.99	17725.380952381
3.99	18741.6666666667
14.99	19368.5833333333
```
13. `挑选不同的price,并且条件为downloads的平均值,且小数点的精度为2位内`
```
SELECT price,ROUND(AVG(downloads),2) FROM fake_apps GROUP BY price;

Query Results
price	ROUND(AVG(downloads),2)
0.0	  15762.26
0.99	15971.51
1.99	16952.6
2.99	17725.38
3.99	18741.67
14.99	19368.58


ROUND() is a function that takes a column name and an integer as an argument. It rounds the values in the column to the number of 
decimal places specified by the integer. Here, we pass the column AVG(downloads) and 2 as arguments. SQL first calculates the 
average for each price and then rounds the result to two decimal places in the result set.
```

14. `四舍五入到整数`
```
SELECT price,ROUND(AVG(downloads)) FROM fake_apps GROUP BY price;

Query Results
price	ROUND(AVG(downloads))
0.0	  15762.0
0.99	15972.0
1.99	16953.0
2.99	17725.0
3.99	18742.0
14.99	19369.0
```
15. 
```
COUNT takes the name of a column(s) as an argument and counts the number of rows where the value(s) is not NULL.
GROUP BY is a clause used with aggregate functions to combine data from one or more columns.
SUM() takes the column name as an argument and returns the sum of all the values in that column.
MAX() takes the column name as an argument and returns the largest value in that column.
MIN() takes the column name as an argument and returns the smallest value in that column.
AVG() takes a column name as an argument and returns the average value for that column.
ROUND() takes two arguments, a column name and the number of decimal places to round the values in that column.
```
