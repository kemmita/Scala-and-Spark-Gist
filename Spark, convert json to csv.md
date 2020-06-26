```sc
package part2dataframes

import org.apache.log4j.{Level, Logger}
import org.apache.spark.sql.SparkSession

object Basics extends App{
  Logger.getLogger("org").setLevel(Level.OFF)
  Logger.getLogger("akka").setLevel(Level.OFF)

  // create spark session
  val spark: SparkSession = SparkSession.builder().appName("Basics").config("spark.master", "local").getOrCreate()

  // obtain the initial json formated code and convert to a df
  val mdf = spark.read.json("src/main/resources/data/movies.json")

  mdf.show()

  // write df to a CSV file
  mdf.write
    .format("csv")
    .option("header", "true")
    .option("sep", ",")
    .save("src/main/resources/data/movies.csv")
}
```
