```
import org.apache.spark.sql.SparkSession
import spark.implicits._

// Start a simple Spark Session
val spark = SparkSession.builder().getOrCreate()

// Load the Netflix Stock CSV File, have Spark infer the data types.
var df = spark.read.option("header", "true").option("inferSchema", "true").csv("Netflix_2011_2016.csv")

// What are the column names?
df.columns
```
