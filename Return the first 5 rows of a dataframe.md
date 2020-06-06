```
// DATAFRAME PROJECT
// Use the Netflix_2011_2016.csv file to Answer and complete
// the commented tasks below!
import org.apache.spark.sql.SparkSession
import spark.implicits._

// Start a simple Spark Session
val spark = SparkSession.builder().getOrCreate()

// Load the Netflix Stock CSV File, have Spark infer the data types.
var df = spark.read.option("header", "true").option("inferSchema", "true").csv("Netflix_2011_2016.csv")

// Print out the first 5 rows.
df.limit(5).show
```
