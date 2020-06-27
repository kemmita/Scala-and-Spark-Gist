```sc
package part2dataframes

import org.apache.log4j.{Level, Logger}
import org.apache.spark.sql.SparkSession
import org.apache.spark.sql.functions._

object Basics extends App{
  Logger.getLogger("org").setLevel(Level.OFF)
  Logger.getLogger("akka").setLevel(Level.OFF)

  // create spark session
  val spark: SparkSession = SparkSession.builder().appName("Basics").config("spark.master", "local").getOrCreate()

  val cdf = spark.read.option("inferSchema", "true").json("src/main/resources/data/movies.json")

  cdf.withColumn("Total_Sales", cdf("US_Gross") + cdf("Worldwide_Gross") + when(cdf("US_DVD_Sales").isNull, 0).otherwise(cdf("US_DVD_Sales"))).show()
}
```
