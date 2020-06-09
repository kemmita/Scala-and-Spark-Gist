```sc
// Import Spark
import org.apache.spark.sql.SparkSession

// Initiate Spark Session
val spark = SparkSession.builder().getOrCreate()

// Read csv file, mark header as true so it is not counted as a row of data, by using inferSchema, 
// Spark will attempt to define the data types.
var df = spark.read.option("header", "true").option("inferSchema", "true").csv("CitiGroup2006_2008")

// this will print the top 10 rows of data
for(line <- df.head(10)){
    println(line)
}

// This will create an array of string containing the column names.
df.columns

// This will provide some general data info such as row count, mean, stdev, min, and max!
df.describe().show()

// select a single columns data
df.select("volume").show()

// select multiple columns data
df.select($"Date", $"Open", $"Close").show()

// to append a new column we will need to create a new dataframe, contining the original 
// columns and data along with the specified new name of the column and what data will be placed in there
val highLowDf = df.withColumn("HighPlusLow", df("High")+df("Low"))

highLowDf.printSchema()

highLowDf.select($"Date", $"High", $"Low", $"HighPlusLow").show()

```
