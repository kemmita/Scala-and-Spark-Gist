1. Below is the main method.
```sc
import common.{DataCleaner, PostgresCommon, SparkCommon}
import org.apache.spark.sql.DataFrame

object ScalaDemo {
  def main(args: Array[String]): Unit = {
    // fetch data from hive table
    val df: DataFrame = SparkCommon.readHiveTable(SparkCommon.createSparkSession())
    // clean the hive table
    val clean_df = DataCleaner.removeDuplicateRows(df)
    // write to postgres table
    val table = "kemmitschema.pg_course"
    PostgresCommon.writeTablePostgres(clean_df, table)
  }
}

```
2. Read from Hive
```sc
def createSparkSession() : SparkSession = {
    Logger.getLogger("org").setLevel(Level.OFF)
    Logger.getLogger("akka").setLevel(Level.OFF)

    // Windows Hadoop Hack
    System.setProperty("hadoop.home.dir", "C:\\winutils")

    // Initiate Spark Session
    SparkSession.builder().appName("Demo").config("spark.master", "local").enableHiveSupport().getOrCreate()
  }

  def readHiveTable(spark: SparkSession): sql.DataFrame = {
    spark.sql("select * from kemmit_hive_db_one.hive_course_table")
  }
```
3. Clean with Spark
```sc
package common

import org.apache.spark.sql.DataFrame

object DataCleaner {
  def removeDuplicateRows(df: DataFrame): DataFrame = {
    val clean_df = df.dropDuplicates()
    clean_df
  }
}
```
4. Write to p[ostgres
```sc
package common

import java.util.Properties

import org.apache.spark.sql
import org.apache.spark.sql.{DataFrame, SaveMode}

  def writeTablePostgres(df: DataFrame, table: String): Unit = {
    df.write
      .mode(SaveMode.Append)
      .format("jdbc")
      .option("url", "jdbc:postgresql://localhost:5432/kemmit")
      .option("dbtable", table)
      .option("user", "postgres")
      .option("password", "password")
      .save()
  }
}

```
