1 Below I show how to join with both scala and Spark.SQL
```sc
import org.apache.spark.sql.SparkSession
import org.apache.log4j.Logger
import org.apache.log4j.Level
import org.apache.spark.sql
import org.apache.spark.sql.functions._

object ScalaDemo {
  Logger.getLogger("org").setLevel(Level.OFF)
  Logger.getLogger("akka").setLevel(Level.OFF)

  def main(args: Array[String]): Unit = {
    // Initiate Spark Session
    val spark = SparkSession.builder().appName("Demo").config("spark.master", "local").getOrCreate()

    // Read csv file
    var df_customer = spark.read.option("header", "true").option("inferSchema", "true").csv("store_customers.csv")
    var df_store = spark.read.option("header", "true").option("inferSchema", "true").csv("store_transactions.csv")

    df_customer.createOrReplaceTempView("customer")
    df_store.createOrReplaceTempView("store")

    // Spark.SQL syntax
    spark.sql("select country, sum(Amount) as TotalSales from customer inner join store on store.CustomerID = customer.CustomerID group by country").show

    // Join the two tables/csv files
    val customer_spend_df: sql.DataFrame = df_customer.join(df_store, df_customer("customerID") === df_store("customerID"), "inner")

    // DataFrame syntax
    customer_spend_df.groupBy("Country").sum("Amount").show()
  }
  
}
```
