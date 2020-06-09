1. If we cannot partition a column like userId, we can use bucketing. Below we divide the data into 20 different files that will be placed in a directoy auto generated with the name specified below.
```
create external table retailcustext_large_bucket (customerid INT, age INT, salary FLOAT,gender String,country String) clustered by (customerid) into 20 buckets location  '/user/russellkemmitdeveloper/retailcust-bucketed/';
```
2. Insert the data
```
from retailcustext_large insert into table retailcustext_large_bucket select customerid,age,salary,gender,country;
```
