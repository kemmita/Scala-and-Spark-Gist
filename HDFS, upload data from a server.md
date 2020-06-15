1. Fisrt create a new dir in hdfs
```
hdfs dfs -mkdir -p /user/russellkemmitdeveloper/ml-100k
```
2. Second copy the data
```
wget http://media.sundog-soft.com/hadoop/ml-100k/u.data
```
3. next copy the data from local to the hadoop dir we created
```
hdfs dfs -copyFromLocal u.data  /user/russellkemmitdeveloper/ml-100k
```
