1. First we will need to enter hive. run command hive in your hadoop server
```
hive
```
2. Once in hive, create a database if needed. 
```
create database if not exists russelldb;
use russelldb;
```
3. Now create a table to mimic your csv structure and data. Based on the csv, we are create column names based on the csv
column names. We will need to specify type, location of the file and delimiter ','. For the location param below,
we do not pass the actual file name, but just the directory conataining the csv "retailstore.csv"
```
create external table retailcustext (age INT, salary FLOAT,gender String,country String, purchased String) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' LOCATION '/user/russellkemmitdeveloper/data/' TBLPROPERTIES ("skip.header.line.count"="1") ;
```
4. Now we can query the data like normal in sql
```
select * from retailcustext;
```
