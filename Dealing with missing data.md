```
// Import Spark
import org.apache.spark.sql.SparkSession
import spark.implicits._

// Initiate Spark Session
val spark = SparkSession.builder().getOrCreate()

// Read csv file, mark header as true so it is not counted as a row of data, by using inferSchema, 
// Spark will attempt to define the data types.
var df = spark.read.option("header", "true").option("inferSchema", "true").csv("ContainsNull.csv")

df.printSchema()

df.show

// this will drop any row contaning a null val in any column.
df.na.drop.show()

// we want to replace all null vals with default vals, we have two columns that contain null vals, 
// first create a new df that will replace null vals in the Name column with J,D
val df2 = df.na.fill("J,D", Array("Name"))
// To fix the last col, we will append 0 to sales cols that appear null
df2.na.fill(0, Array("Sales")).show

```
