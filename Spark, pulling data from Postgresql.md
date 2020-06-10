```sc
import java.util.Properties

import org.apache.spark.sql.SparkSession
import org.apache.log4j.Logger
import org.apache.log4j.Level
import org.apache.spark
import org.apache.spark.sql
import org.apache.spark.sql.functions._

object ScalaDemo {
  def main(args: Array[String]): Unit = {
    Logger.getLogger("org").setLevel(Level.OFF)
    Logger.getLogger("akka").setLevel(Level.OFF)

    // Windows Hadoop Hack
    System.setProperty("hadoop.home.dir", "C:\\winutils")

    // Initiate Spark Session
    val spark = SparkSession.builder().appName("Demo").config("spark.master", "local").enableHiveSupport().getOrCreate()

    // prepare Database Props
    val connectionProps = new Properties()
    connectionProps.put("user","postgres")
    connectionProps.put("password","password")

    // Create DataFrame from PG table structure
    val pg_df = spark.read.jdbc("jdbc:postgresql://localhost:5432/kemmit","kemmitschema.course_catalog",connectionProps)

    pg_df.show()
  }

}

```
