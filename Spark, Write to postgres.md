1. We will obtain some data from a json file and write it to our rdbm.
```sc
package part2dataframes

import org.apache.log4j.{Level, Logger}
import org.apache.spark.sql.SparkSession

object Basics extends App{
  Logger.getLogger("org").setLevel(Level.OFF)
  Logger.getLogger("akka").setLevel(Level.OFF)

  // create spark session
  val spark: SparkSession = SparkSession.builder().appName("Basics").config("spark.master", "local").getOrCreate()

  val mdf = spark.read.json("src/main/resources/data/movies.json")

  mdf.show()

  mdf.write
    .format("jdbc")
    .option("driver", "org.postgresql.Driver")
    .option("url", "jdbc:postgresql://localhost:5432/rtjvm")
    .option("user", "docker")
    .option("password", "docker")
    .option("dbtable", "public.movies")
    .save()
}
```
