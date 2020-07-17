```sc
// Import Spark
import org.apache.spark.sql.SparkSession
import org.apache.spark.ml.regression.LinearRegression
import org.apache.spark.ml.feature.VectorAssembler
import org.apache.spark.ml.linalg.Vectors

// Initiate Spark Session
val spark = SparkSession.builder().getOrCreate()

// Read csv data file
val df = spark.read.option("header", "true").option("inferSchema", "true").format("csv").load("Clean_USA_Housing.csv")

// Define the new df to consist of only numeric values. Also define the label "Price" Price will be the label and we will use the value
// within Price to calculate the other numeric cols and how they correlate to the price in question.
val pdf = (df.select(df("Price").as("label"),
            $"Avg Area Income", $"Avg Area House Age",
            $"Avg Area Number of Rooms", $"Avg Area Number of Bedrooms", $"Area Population"))

// Create a new vecotr of the defined columns. These columns will be calculated against price to create a regression line.
val assembler = new VectorAssembler().setInputCols(Array("Avg Area Income", "Avg Area House Age", "Avg Area Number of Rooms", "Avg Area Number of Bedrooms", "Area Population")).setOutputCol("features")

// Prepare data from ML, there will be 2 cols in this df, one will be our label "Price", the other will be a vector
// consisting of the defined numeric cols above.
val output = assembler.transform(pdf).select($"label", $"features")

// Create regression model
val lrModel = new LinearRegression().fit(output)

val trainingSummary = lrModel.summary
```
