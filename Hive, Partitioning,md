1. Enter Hive
```
hive
```
2. Create db if not created.
```
create database if not exists kemmit_large;
```
3. Set use
```
use kemmit_large;
```
4. Create initial table that will hold all of the data Million plus records/rows
```
create external table retailcustext_large (customerid INT, age INT, salary FLOAT,gender String,country String) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' LOCATION '/user/russellkemmitdeveloper/retail/' TBLPROPERTIES ("skip.header.line.count"="1") ;
```
5. Set hive partition rules
```
set hive.exec.dynamic.partition=true;
set hive.exec.dynamic.partition.mode=nonstrict;
```
6. Now create the sub directories that will contain data according to the name of the countr
```
create external table retailcustext_large_partitioned (customerid INT, age INT, salary FLOAT,gender String) partitioned by (country String) location  '/user/russellkemmitdeveloper/retail-partitioned/';
```
7. After running the above command, you can see in hdfs that the directories were created.
```
hdfs dfs -ls /user/russellkemmitdeveloper/retail-partitioned
// result
drwxr-xr-x   - russellkemmitdeveloper hadoop          0 2020-06-09 19:32 /user/russellkemmitdeveloper/retail-partitioned/country=England
drwxr-xr-x   - russellkemmitdeveloper hadoop          0 2020-06-09 19:32 /user/russellkemmitdeveloper/retail-partitioned/country=France
drwxr-xr-x   - russellkemmitdeveloper hadoop          0 2020-06-09 19:32 /user/russellkemmitdeveloper/retail-partitioned/country=Germany
```
8. Now insert data into the sub directories from our intial "Huge" table we had
```
insert into table retailcustext_large_partitioned partition(country) select * from retailcustext_large;
```
9. Now when you specify the country in the query, you will only be querying that sub direcotry associated with the country in question.
```
select salary from retailcustext_large_partitioned where country = "Germany" AND Age > 65 AND Gender = "Male";
```
