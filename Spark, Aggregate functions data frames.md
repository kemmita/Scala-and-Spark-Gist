```sc
// Import Spark
import org.apache.spark.sql.SparkSession
import spark.implicits._

// Initiate Spark Session
val spark = SparkSession.builder().getOrCreate()

// Read csv file, mark header as true so it is not counted as a row of data, by using inferSchema, 
// Spark will attempt to define the data types.
var df = spark.read.option("header", "true").option("inferSchema", "true").csv("Sales.csv")

df.printSchema()

df.show

// below methods will calculate the mean and sum of numeric values within the csv grouped by each company
df.groupBy("Company").mean().show
df.groupBy("Company").sum().show
df.groupBy("Company").max().show


// we can also perform the same agg functions by targeting the columns individually.
df.select(sum("Sales")).show
df.select(mean("Sales")).show
df.select(sumDistinct("Sales")).show


df.orderBy($"Sales".desc).show
```
