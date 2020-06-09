```sc
// Import Spark
import org.apache.spark.sql.SparkSession
import spark.implicits._

// Initiate Spark Session
val spark = SparkSession.builder().getOrCreate()

// Read csv file, mark header as true so it is not counted as a row of data, by using inferSchema, 
// Spark will attempt to define the data types.
var df = spark.read.option("header", "true").option("inferSchema", "true").csv("CitiGroup2006_2008")

df.printSchema()

// Simple filter on the dataframe, both return the same data, top uses scala notation and botom uses SQL wihout the WHERE, it is implied
// The ending show method is used to simply show the data in the terminal, this can be removed.
df.filter($"Close" > 530 && $"Close" < 550).show()
df.filter("Close > 530 AND Close < 550").show()

// Instead of showing the data, lets collect it into an array of sql rows.
val CH_low = df.filter("Close < 480 AND HIGH < 480").collect()

// And we can then convert it into a list if we want to.
val li = CH_low.toList

// count number of rows returned meeting filter criteria.
val c = df.filter("Close< 480 AND High < 480").count()
```
