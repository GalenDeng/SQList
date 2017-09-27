# SQL学习---codecademy (2017.09.27)
`SQLite 是一个开源的嵌入式关系数据库`
## fifth lesson

1. `显示十行数据`
```
Introduction:
/作用：Select ten rows from the flights table./

SELECT * FROM Flights LIMIT 10;

result:

id	carrier	origin	destination	flight_num	flight_time	tail_num	dep_time	arr_time	dep_delay	arr_delay	taxi_out	taxi_in	distance	cancelled	diverted	dep_day_of_week	dep_month	dep_date
17107	MQ	  SNA     	SJC	        3186	      62	        N829AE	4/7/2005 15:24:00	4/7/2005 16:39:00	-1	0	9	4	342	N	N	Thursday	2005-04	4/7/2005
19471	DL	  JFK	      MCO	        1998	      134	        N186DN	6/6/2000 17:15:00	6/6/2000 19:57:00	0	-13	23	5	944	N	N	Tuesday	2000-06	6/6/2000
194	  AA	    MIA	    BWI	        1898	      125	        N3BBAA	10/10/2002 13:36:00	10/10/2002 16:13:00	-4	0	24	8	946	N	N	Thursday	2002-10	10/10/2002
19905	HP	  ORD	      PHX	        647	        189	        N622AW	2/20/2002 7:31:00	2/20/2002 10:31:00	-7	6	18	33	1440	N	N	Tuesday	2002-02	2/20/2002
11155	WN	  SAT	      HRL	        173	        40	        N442WN	1/27/2005 18:45:00	1/27/2005 19:32:00	30	27	5	2	233	N	N	Thursday	2005-01	1/27/2005
4690	DL	  PNS	      ATL	        772	        52	        N931DL	6/15/2005 6:16:00	6/15/2005 8:29:00	-4	-9	10	11	272	N	N	Tuesday	2005-06	6/15/2005
6886	DH	  DAY	      CVG       	6153	      26	        N405FJ	5/15/2004 18:31:00	5/15/2004 19:12:00	-11	-13	8	6	64	N	N	Saturday	2004-05	5/15/2004
3674	DL	  SLC	      EWR	        2166	      213	        N371DA	12/23/2000 16:43:00	12/23/2000 22:43:00	3	-13	18	9	1968	N	N	Saturday	2000-12	12/23/2000
5538	DL	  ATL	      ABQ	        1589	      188	        N388DA	3/27/2003 18:47:00	3/27/2003 20:12:00	-3	1	12	5	1269	N	N	Thursday	2003-03	3/27/2003
510	  WN	  RNO	      SJC	        1466	       47	        N637SW	12/13/2000 15:00:00	12/13/2000 15:56:00	0	1	5	4	188	N	N	Wednesday	2000-12	12/13/2000
```
2. `(SELECT code FROM airports WHERE elevation < 2000 : 为子查询的结果集，最后的过滤要根据这个条件来过滤`
```
SELECT * FROM flights WHERE origin in (SELECT code FROM airports WHERE elevation < 2000);
```