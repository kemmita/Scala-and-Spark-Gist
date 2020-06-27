```scpackage part2dataframes

import org.apache.log4j.{Level, Logger}
import org.apache.spark.sql.SparkSession

object Basics extends App{
  Logger.getLogger("org").setLevel(Level.OFF)
  Logger.getLogger("akka").setLevel(Level.OFF)

  // create spark session
  val spark: SparkSession = SparkSession.builder().appName("Basics").config("spark.master", "local").getOrCreate()

  val cdf = spark.read.option("inferSchema", "true").json("src/main/resources/data/cars.json")
  
  cdf
    .where("Origin = 'USA' AND Horsepower > 130 AND Miles_per_Gallon > 12.0")
    .show()

}


```
