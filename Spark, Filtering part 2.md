1. For some weird reason I am having trouble filtering my current data, I have found that a slight change has now enabled it to work, not the filter expressions.
```sc
package part2dataframes

import org.apache.log4j.{Level, Logger}
import org.apache.spark.sql.SparkSession

object Basics extends App{
  Logger.getLogger("org").setLevel(Level.OFF)
  Logger.getLogger("akka").setLevel(Level.OFF)

  // create spark session
  val spark: SparkSession = SparkSession.builder().appName("Basics").config("spark.master", "local").getOrCreate()

  val cdf = spark.read.option("inferSchema", "true").json("src/main/resources/data/cars.json")


 cdf.where("Origin != 'USA'").show()
 cdf.filter("Origin != 'USA'").show()
}
```
