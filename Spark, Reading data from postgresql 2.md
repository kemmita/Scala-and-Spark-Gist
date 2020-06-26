```sc
package part2dataframes

import org.apache.log4j.{Level, Logger}
import org.apache.spark.sql.SparkSession

object Basics extends App{
  Logger.getLogger("org").setLevel(Level.OFF)
  Logger.getLogger("akka").setLevel(Level.OFF)

  // create spark session
  val spark: SparkSession = SparkSession.builder().appName("Basics").config("spark.master", "local").getOrCreate()

  val edf = spark.read
    .format("jdbc")
    .option("driver", "org.postgresql.Driver")
    .option("url", "jdbc:postgresql://localhost:5432/rtjvm")
    .option("user", "docker")
    .option("password", "docker")
    .option("dbtable", "public.employees")
    .load()

  edf.show()
}
```
