```sc

// Import Spark
import org.apache.spark.sql.SparkSession

// Initiate Spark Session
val spark = SparkSession.builder().getOrCreate()

// Read csv file, mark header as true so it is not counted as a row of data, by using inferSchema, 
// Spark will attempt to define the data types.
var df = spark.read.option("header", "true").option("inferSchema", "true").csv("original.csv")

df.createOrReplaceTempView("customer")

// Spark.SQL syntax
spark.sql("select country, avg(Salary) as MeanSalary, avg(age) as MeanAge from customer where Gender = 'Female' and Age > 18 group by country").show

// Spark.Dataframe syntax
df.filter($"Gender" === "Female" && $"Age" > 18).groupBy("Country").mean("Salary", "Age").show
```
