<b>Important</b>:<br>

This is the second part of the gist which is not done in `Atom`. Please use `Databricks` and `Zeppelin` instead.

## Intermediary level in Spark-Scala using Databricks and Zeppelin (notebooks)

We will perform two installations before we start programming in `Spark-Scala`.<br>

I recommend using `Zeppelin` if you want to use a secure enviroment on `Localhost` for data security compliance.<br>

I recommend using `Databricks` if you want to use a programming environment in the `Cloud` accessible from everywhere.

## 1. Installations

### DataBricks (Cloud deployment)

To use the free version of `Databricks`, go to https://community.cloud.databricks.com, create a free account and log in.<br>

<details>
<summary>🔴 See dashboard</summary>
<p> 
  
[![isaac-arnault-spark-scala-15.png](https://i.postimg.cc/DzkH5f7k/isaac-arnault-spark-scala-15.png)](https://postimg.cc/NKDdjcyp)

</p>
</details>

Go to Clusters > Create cluster

<details>
<summary>🔴 See cluster configuration</summary>
<p> 
  
[![isaac-arnault-spark-scala-16.png](https://i.postimg.cc/26jHXVJJ/isaac-arnault-spark-scala-16.png)](https://postimg.cc/d7XmhtJm)

</p>
</details>

Go to Workspace > Users > Create notebook

<details>
<summary>🔴 See notebook configuration</summary>
<p> 
  
[![isaac-arnault-spark-scala-17.png](https://i.postimg.cc/sgFTCnq5/isaac-arnault-spark-scala-17.png)](https://postimg.cc/8jHRhb1C)

</p>
</details>

Now you are ready to work with `Databricks`. Now let's install `Apache Zeppelin`.

### Apache Zeppelin installation (Localhost deployment)

If you haven't performed `Apache Zeppelin` yet, follow this <a target="blank" href="https://gist.github.com/isaacarnault/19979a97be64192bb15b7b5e2e351889">gist</a> I wrote few months ago.<br>

Once the soft is extracted from the tarball and installed on your desktop, perform the following to launch it:<br>
- Open your terminal using `Ctrl + Alt +t`
- Go to the .bin folder of `Apache Zeppelin`
- execute `$ ./zeppelin.sh` in your terminal and wait for a minute until the application starts

<details>
<summary>🔴 See on terminal</summary>
<p> 
  
[![1.png](https://i.postimg.cc/Kv0YW4T4/1.png)](https://postimg.cc/xcbYJftS)

</details>

- Use `localhost:8080/` in your web browser to access `Apache Zeppelin` from your computer<br>

- Go to Notebook > Create New Note

<details>
<summary>🔴 See notebook configuration</summary>
<p> 
  
[![isaac-arnault-spark-scala-20.png](https://i.postimg.cc/qBWxgy3k/isaac-arnault-spark-scala-20.png)](https://postimg.cc/PNzwRLyc)

</p>
</details>

Now you are ready to work with `Apache Zeppelin`.

<details>
<summary>🔴 See notebook</summary>
<p> 
  
[![isaac-arnault-spark-scala-20.png](https://i.postimg.cc/qBWxgy3k/isaac-arnault-spark-scala-20.png)](https://postimg.cc/PNzwRLyc)

</p>
</details>

We are now ready to start programming.

## 2. Programming in Spark-Scala

We will launch our `Spark-Scala` commands from both environments `Apache Zeppelin` and `Databricks` so that you can see how they render on both.<br>

Upload <b>CitiGroup2006_2008.csv</b> to your `Databricks` and `Zeppelin` environments before you proceed.

### 1. Loading a csv file as dataframe

```r
import org.apache.spark.sql.SparkSession
val spark = SparkSession.builder().getOrCreate()
val df = spark.read.option("header","true").option("inferSchema","true").csv("/home/zaki/Desktop/gist/CitiGroup2006_2008.csv")

df.show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p> 
  
[![isaac-arnault-zeppelin-1.png](https://i.postimg.cc/2SDV3F7N/isaac-arnault-zeppelin-1.png)](https://postimg.cc/dL5qxCf5)

</p>
</details>

```r
// OPTION 1
val df = sqlContext.read.format("csv")
  .option("header", "true")
  .option("inferSchema", "true")
  .load("/FileStore/tables/CitiGroup2006_2008.csv")
  
display(df)
  ```
  
<details>
<summary>🔴 See in Databricks - OPTION 1</summary>
<p>
  
[![11.png](https://i.postimg.cc/kgppcrwZ/11.png)](https://postimg.cc/75S9HWFM)

</p>
</details>

```r
// OPTION 2
val spark = SparkSession.builder().getOrCreate()
val df = spark.read.option("header","true").option("inferSchema","true").csv("/FileStore/tables/CitiGroup2006_2008.csv")

df.show()
```

<details>
<summary>🔴 See in Databricks - OPTION 2</summary>
<p>
  
[![16.png](https://i.postimg.cc/L5mVBvPh/16.png)](https://postimg.cc/gXBRGVNP)

</p>
</details>
 
### 2. Get column names

```r
df.columns
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-databricks-2.png](https://i.postimg.cc/3JcQcKWS/isaac-arnault-databricks-2.png)](https://postimg.cc/LnLWqFtL)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p>

[![isaac-arnault-zeppelin-2.png](https://i.postimg.cc/prr1fFQ2/isaac-arnault-zeppelin-2.png)](https://postimg.cc/7JvVDbQc)

</p>
</details>
  
### 3. Get basic statistics

```r
df.describe().show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p> 

[![isaac-arnault-zeppelin-3.png](https://i.postimg.cc/cHXbtmn9/isaac-arnault-zeppelin-3.png)](https://postimg.cc/zbHj9TpK)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p>

[![isaac-arnault-databricks-3.png](https://i.postimg.cc/zvTpSFbY/isaac-arnault-databricks-3.png)](https://postimg.cc/q6M8pnx1)

</p>
</details>

### 4. Select one column and show some data

```r
df.select("Volume").show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p> 
  
[![isaac-arnault-zeppelin-4.png](https://i.postimg.cc/9fV2GLDC/isaac-arnault-zeppelin-4.png)](https://postimg.cc/mPdK4N35)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 
  
[![isaac-arnault-databricks-4.png](https://i.postimg.cc/435gwpct/isaac-arnault-databricks-4.png)](https://postimg.cc/p9p4LhqX)

</p>
</details>
  
### 5. Select two or more columns and show some data

```r
df.select($"Date", $"Low", $"Volume").show(10)
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-5.png](https://i.postimg.cc/Rhf6WP3K/isaac-arnault-zeppelin-5.png)](https://postimg.cc/bSyNM99w)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-5.png](https://i.postimg.cc/pVnncd0r/isaac-arnault-databricks-5.png)](https://postimg.cc/3WYRd3QQ)

</p>
</details>

### 6. Create a new column from a substraction of two columns

```r
df.withColumn("HighMinusOpen", df("High")-df("Open")).show(5)
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-6.png](https://i.postimg.cc/9MKMGssz/isaac-arnault-zeppelin-6.png)](https://postimg.cc/Q9ghDY8r)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-6.png](https://i.postimg.cc/3RdN03SP/isaac-arnault-databricks-6.png)](https://postimg.cc/hzRcHRqr)

</p>
</details>

### 7. Store operation performed in step 6 as a new dataframe

```r
val df2 = df.withColumn("HighMinusOpen", df("High")-df("Open"))
df2.show(5)
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-7.png](https://i.postimg.cc/76gnCvBM/isaac-arnault-zeppelin-7.png)](https://postimg.cc/JDzkgFCG)

</p>
</details>

```r
df.withColumn("HighMinusOpen", df("High")-df("Open")).show(5)
```
  
<details>
<summary>🔴 See in Databricks</summary>
<p>

[![isaac-arnault-databricks-7.png](https://i.postimg.cc/C5SHkvXy/isaac-arnault-databricks-7.png)](https://postimg.cc/hzZdq0KM)

</p>
</details>

### 8. Print our new dataframe Schema

```r
df2.printSchema()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-8.png](https://i.postimg.cc/65HL4fhS/isaac-arnault-zeppelin-8.png)](https://postimg.cc/Ln1ZrfwB)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-8.png](https://i.postimg.cc/4xmv6HL3/isaac-arnault-databricks-8.png)](https://postimg.cc/QFZWsCrL)

</p>
</details>

### 9. Rename one column of our dataframe and save it as a new dataframe

```r
val df3 = df2.withColumnRenamed("HighMinusOpen","HmO")
df3.show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-9.png](https://i.postimg.cc/hv1vhcVR/isaac-arnault-zeppelin-9.png)](https://postimg.cc/2L3rKpH0)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-9.png](https://i.postimg.cc/NFBG3SSJ/isaac-arnault-databricks-9.png)](https://postimg.cc/ygpz9QVc)

</p>
</details>

### 10. Dataframe operations
  > Filtering on a column - Using Scala "$" instead of Spark SQL

```r
import spark.implicits._
df.filter($"Open">480).show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-10.png](https://i.postimg.cc/J016q6XC/isaac-arnault-zeppelin-10.png)](https://postimg.cc/TL4J2cQt)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-10.png](https://i.postimg.cc/cCXD5R7g/isaac-arnault-databricks-10.png)](https://postimg.cc/9wwtDqnC)

</p>
</details>

  > Filtering on a column - Using Spark SQL

```r
import spark.implicits._
df.filter("Open>480").show()  
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
    
[![14.png](https://i.postimg.cc/J4PrRn4k/14.png)](https://postimg.cc/KR3SNmTG)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-10-2.png](https://i.postimg.cc/cC4hYKqs/isaac-arnault-databricks-10-2.png)](https://postimg.cc/1n2D135T)

</p>
</details>

  > Filtering on multiple columns - Using Scala "$" instead of Spark SQL

```r
import spark.implicits._
df.filter($"Low"<481 && $"High">484).show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
    
[![isaac-arnault-zeppelin-10-3.png](https://i.postimg.cc/SQvv0pwJ/isaac-arnault-zeppelin-10-3.png)](https://postimg.cc/yW0P926H)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-10-3.png](https://i.postimg.cc/PJ931mmm/isaac-arnault-databricks-10-3.png)](https://postimg.cc/fS7fNSqL)

</p>
</details>

  > Filtering on multiple columns - Using Spark SQL

```r
df.filter("Low<481 AND High>484").show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-10-4.png](https://i.postimg.cc/WpdPqSVq/isaac-arnault-zeppelin-10-4.png)](https://postimg.cc/NLvnW65Q)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-10-4.png](https://i.postimg.cc/4yDPYXgP/isaac-arnault-databricks-10-4.png)](https://postimg.cc/0KCD3RrK)

</p>
</details>

<b>Important</b> `df.filter` in `Spark` is a <b>transformation</b> while a `.show()` is an <b>action</b>.<br>

  > Filtering on multiple columns and collect the results as an array - Using Scala

```r
import spark.implicits._
val CH_compare = df.filter("Low<481 AND High>484").collect()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-10-5.png](https://i.postimg.cc/bJwyhKwJ/isaac-arnault-zeppelin-10-5.png)](https://postimg.cc/SXHFL18F)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-10-5.png](https://i.postimg.cc/TP9dBRGF/isaac-arnault-databricks-10-5.png)](https://postimg.cc/B8jfKfjB)

</p>
</details>

  > Filtering on multiple columns and check how many results are returned - Using Scala

```r
import spark.implicits._
val CH_compare = df.filter("Low<481 AND High>484").count()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-10-6.png](https://i.postimg.cc/JnRDtd09/isaac-arnault-zeppelin-10-6.png)](https://postimg.cc/R3bVDdcR)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-10-6.png](https://i.postimg.cc/QC1pvY4C/isaac-arnault-databricks-10-6.png)](https://postimg.cc/tnRZxkHG)

</p>
</details>

  > 10.7 Filtering on a column for equality 

```r
import spark.implicits._
df.filter($"Low" === 484).show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-databricks-10-7.png](https://i.postimg.cc/qBxqZdQn/isaac-arnault-databricks-10-7.png)](https://postimg.cc/pyyPp4wX)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p>

[![isaac-arnault-databricks-10-7.png](https://i.postimg.cc/qBxqZdQn/isaac-arnault-databricks-10-7.png)](https://postimg.cc/pyyPp4wX)

</p>
</details>

  > 10.8 Dataframe operations - Correlation (Pearson)

```r
import spark.implicits._
df.select(corr("Open","Close")).show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-10-8.png](https://i.postimg.cc/rmKXLB4M/isaac-arnault-zeppelin-10-8.png)](https://postimg.cc/8JQnRnw0)

</p>
</details>

```r
df.stat.corr("Open", "Close")
```

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-10-8.png](https://i.postimg.cc/438brdV2/isaac-arnault-databricks-10-8.png)](https://postimg.cc/wtmmN9WD)

</p>
</details>

  > 11 Dataframes operations - Group By and Aggregate (New dataset)

Upload <b>Sales.csv</b> to your `Databricks` and `Zeppelin` environments before you proceed as follows.

```r
import org.apache.spark.sql.SparkSession
Upload <b>Sales.csv</b> to your `Databricks` and `Zeppelin` environments before you proceed.

val spark = SparkSession.builder().getOrCreate()
val df_Sales = spark.read.option("header","true").option("inferSchema","true").csv("/home/zaki/Desktop/Sales.csv")

df_Sales.show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![18.png](https://i.postimg.cc/0yHxTB2R/18.png)](https://postimg.cc/NKTWTbHp)

</p>
</details>

  
```r
val df_Sales = sqlContext.read.format("csv")
  .option("header", "true")
  .option("inferSchema", "true")
  .load("/FileStore/tables/Sales.csv")

display(df_Sales)
```

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![17.png](https://i.postimg.cc/90tCsXzJ/17.png)](https://postimg.cc/V06xC8qC)

</p>
</details>

  > Dataframes operations - Group By and Aggregate (Count)

```r
df_Sales.groupBy("Company").count().show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>

[![isaac-arnault-zeppelin-11-1.png](https://i.postimg.cc/VN35rP8L/isaac-arnault-zeppelin-11-1.png)](https://postimg.cc/yJy7t5xw)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p>
  
[![isaac-arnault-databricks-11-1.png](https://i.postimg.cc/HWb8MnjG/isaac-arnault-databricks-11-1.png)](https://postimg.cc/Wtb4L2MS)

</p>
</details>

  > Dataframes operations - Group By and Aggregate (Mean)

```r
df_Sales.groupBy("Company").mean().show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>

[![isaac-arnault-zeppelin-11-2.png](https://i.postimg.cc/CKZzxL9Q/isaac-arnault-zeppelin-11-2.png)](https://postimg.cc/yJHVfB1m)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p>

[![isaac-arnault-databricks-11-2.png](https://i.postimg.cc/cC7KG9P1/isaac-arnault-databricks-11-2.png)](https://postimg.cc/H8xWQ2pF)

</p>
</details>

  > Dataframes operations - Group By (common statistics)

```r
df_Sales.groupBy("Company").min().show()
df_Sales.groupBy("Company").max().show()
df_Sales.groupBy("Company").sum().show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>

[![isaac-arnault-zeppelin-11-3.png](https://i.postimg.cc/rwWRcpWF/isaac-arnault-zeppelin-11-3.png)](https://postimg.cc/DSvwPnBt)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-11-3.png](https://i.postimg.cc/65F4DZ8m/isaac-arnault-databricks-11-3.png)](https://postimg.cc/xcydmcyv)

</p>
</details>

  > Dataframes operations - Aggregate (sum)

```r
df_Sales.select(sum("Sales")).show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>

[![isaac-arnault-databricks-11-4.png](https://i.postimg.cc/bvyyMY95/isaac-arnault-databricks-11-4.png)](https://postimg.cc/yDGC3H5h)

</p>
</details>

```r
import sqlContext.implicits._
import org.apache.spark.sql.functions._

df_Sales.select(sum("Sales")).show()
```

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-11-4.png](https://i.postimg.cc/wv36qWPc/isaac-arnault-databricks-11-4.png)](https://postimg.cc/Fd5tGxh7)

</p>
</details>

  > Dataframes operations - Aggregate (other useful operations)

```r
df_Sales.select(countDistinct("Sales")).show()
df_Sales.select(sumDistinct("Sales")).show()
df_Sales.select(variance("Sales")).show()
df_Sales.select(stddev("Sales")).show() // standard deviation
df_Sales.select(collect_set("Sales")).show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-11-5.png](https://i.postimg.cc/t4SqKQvC/isaac-arnault-zeppelin-11-5.png)](https://postimg.cc/Sn9b95pw)

</p>
</details>

  
```r
import sqlContext.implicits._
import org.apache.spark.sql.functions._

df_Sales.select(countDistinct("Sales")).show()
df_Sales.select(sumDistinct("Sales")).show()
df_Sales.select(variance("Sales")).show()
df_Sales.select(stddev("Sales")).show() // standard deviation
df_Sales.select(collect_set("Sales")).show()
```

<details>
<summary>🔴 See in Databricks</summary>
<p> 
  
[![isaac-arnault-databricks-11-5.png](https://i.postimg.cc/FHsFCsZB/isaac-arnault-databricks-11-5.png)](https://postimg.cc/xchScQBv)

</p>
</details>

  > Dataframes operations - Order By (using Spark SQL)

```r
df_Sales.show()
df_Sales.orderBy("Sales").show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-11-6.png](https://i.postimg.cc/d3HNqBbd/isaac-arnault-zeppelin-11-6.png)](https://postimg.cc/LgP3Dz66)

</p>
</details>

```r
import sqlContext.implicits._
import org.apache.spark.sql.functions._

df_Sales.show()
df_Sales.orderBy("Sales").show()
```

<details>
<summary>🔴 See in Databricks</summary>
<p>
  
[![isaac-arnault-databricks-11-6.png](https://i.postimg.cc/HnsPDKhd/isaac-arnault-databricks-11-6.png)](https://postimg.cc/8J9bLyG0)

</p>
</details>

> Dataframes operations - Order By (using scala)

```r
import org.apache.spark.sql.SparkSession

val spark = SparkSession.builder().getOrCreate()
val df_Null = spark.read.option("header","true").option("inferSchema","true").csv("/home/zaki/Desktop/ContainsNull.csv")

df_Null.show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-11-7.png](https://i.postimg.cc/6pdVccM0/isaac-arnault-zeppelin-11-7.png)](https://postimg.cc/68pG5rJ2)

</p>
</details>

```r
val df_Null = sqlContext.read.format("csv")
  .option("header", "true")
  .option("inferSchema", "true")
  .load("/FileStore/tables/ContainsNull.csv")

display(df_Null)
```

<details>
<summary>🔴 See in Databricks</summary>
<p>

[![isaac-arnault-databricks-11-7.png](https://i.postimg.cc/CxyHbXs5/isaac-arnault-databricks-11-7.png)](https://postimg.cc/KRNM29Vh)

</p>
</details>

  > Dataframes operations - Missing data (New dataset)

Upload <b>ContainsNull.csv</b> to your `Databricks` and `Zeppelin` environments before you proceed as follows.
  
```r
df_Sales.show()
df_Sales.orderBy($"Sales".desc).show(3)
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-12.png](https://i.postimg.cc/sX9C4DmT/isaac-arnault-zeppelin-12.png)](https://postimg.cc/wyvr6zSN)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![15.png](https://i.postimg.cc/dtTbxVZF/15.png)](https://postimg.cc/ZC4s9ZLs)

</p>
</details>

  > Dataframes operations - Missing data (Drop)

```r
df_Null.show()
df_Null.na.drop().show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>

[![isaac-arnault-zeppelin-12-1.png](https://i.postimg.cc/7PBDbhWV/isaac-arnault-zeppelin-12-1.png)](https://postimg.cc/6TGFmWw2)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p>
  
[![isaac-arnault-databricks-12-1.png](https://i.postimg.cc/mk6GnpHq/isaac-arnault-databricks-12-1.png)](https://postimg.cc/64RS20zL)

</p>
</details>

  > Dataframes operations - Missing data (Fill)
  
```r
df_Null.show()
df_Null.na.fill(42).show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>

[![isaac-arnault-zeppelin-12-2.png](https://i.postimg.cc/NGxVjn5v/isaac-arnault-zeppelin-12-2.png)](https://postimg.cc/qgzQmjs1)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-12-2.png](https://i.postimg.cc/YSc83Nhx/isaac-arnault-databricks-12-2.png)](https://postimg.cc/hXr94d8J)

</p>
</details>

  > Dataframes operations - Missing data (Fill a specific column, "Name", with a string)
  
```r
df_Null.show()
val clean_dfX = df_Null.na.fill("Name X", Array("Name")) 
clean_dfX.show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-12-3.png](https://i.postimg.cc/bNMVtKbG/isaac-arnault-zeppelin-12-3.png)](https://postimg.cc/ZC8LkswZ)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p>

[![isaac-arnault-databricks-12-3.png](https://i.postimg.cc/L4QNcrxy/isaac-arnault-databricks-12-3.png)](https://postimg.cc/bdbxbFcb)

</p>
</details>

  > Dataframes operations - Missing data (Fill a specific column, "Sales", with an integer)

```r
df_Null.show()
val clean_dfY = clean_dfX.na.fill(50, Array("Sales"))
clean_dfY.show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-databricks-12-4.png](https://i.postimg.cc/hvYsVdJF/isaac-arnault-databricks-12-4.png)](https://postimg.cc/n9vqJMYT)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p>

[![isaac-arnault-databricks-12-4.png](https://i.postimg.cc/hvYsVdJF/isaac-arnault-databricks-12-4.png)](https://postimg.cc/n9vqJMYT)

</p>
</details>

  > Dataframes operations - Filling missing data in multiple columns simulateously

```r
df_Null.show()
val clean_dfZ = df_Null.na.fill(60, Array("Sales"))
clean_dfZ.na.fill("Name Z", Array("Name")).show()
```

<details>
<summary>🔵 See in Zeppelin</summary>
<p>

[![isaac-arnault-zeppelin-12-5.png](https://i.postimg.cc/HW6hpJk9/isaac-arnault-zeppelin-12-5.png)](https://postimg.cc/jCJXcSND)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p> 

[![isaac-arnault-databricks-12-5.png](https://i.postimg.cc/4yywK5xb/isaac-arnault-databricks-12-5.png)](https://postimg.cc/n98qgq7C)

</p>
</details>

#### 13 Dates and Timestamps
Let's re-take <br>CitiGroup2006_2008.csv</b> dataset once again for this part of the gist.<br>

<details>

```r
val Date_Time = sqlContext.read.format("csv")
  .option("header", "true")
  .option("inferSchema", "true")
  .load("/home/zaki/Downloads/CitiGroup2006_2008.csv")

Date_Time.show()
```

<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-13.png](https://i.postimg.cc/s2w7vfjd/isaac-arnault-zeppelin-13.png)](https://postimg.cc/06Kb4sKc)

</p>
</details>

```r
val Date_Time = sqlContext.read.format("csv")
  .option("header", "true")
  .option("inferSchema", "true")
  .load("/FileStore/tables/CitiGroup2006_2008.csv")

display(Date_Time)
```
<details>
<summary>🔴 See in Databricks</summary>
<p> 
  
[![isaac-arnault-zeppelin-13.png](https://i.postimg.cc/s2w7vfjd/isaac-arnault-zeppelin-13.png)](https://postimg.cc/06Kb4sKc)

</p>
</details>

  > Dates and Timestamps - returns only the month from a timestamp

<details>
  
```r
Date_Time.select(month(Date_Time("Date"))).show()
```
<summary>🔵 See in Zeppelin</summary>
<p> 
  
[![isaac-arnault-zeppelin-13-1.png](https://i.postimg.cc/59Z7xgK5/isaac-arnault-zeppelin-13-1.png)](https://postimg.cc/K4DrfP24)

</p>
</details>

```r
import sqlContext.implicits._
import org.apache.spark.sql.functions._
Date_Time.select(month(Date_Time("Date"))).show()
```
<details>
<summary>🔴 See in Databricks</summary>
<p> 
    
[![isaac-arnault-databricks-13-1.png](https://i.postimg.cc/VLn75t2x/isaac-arnault-databricks-13-1.png)](https://postimg.cc/fJW7rVzC)

</p>
</details>

> Dates and Timestamps - returns only the year from a timestamp

<details>
  
```r
Date_Time.select(year(Date_Time("Date"))).show()
```

<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-13-2.png](https://i.postimg.cc/SR8G2016/isaac-arnault-zeppelin-13-2.png)](https://postimg.cc/4Hfcq0gy)

</p>
</details>

```r
import sqlContext.implicits._
import org.apache.spark.sql.functions._
Date_Time.select(year(Date_Time("Date"))).show()
```

<details>
<summary>🔴 See in Databricks</summary>
<p> 
  
[![isaac-arnault-databricks-13-2.png](https://i.postimg.cc/qRWLvBwB/isaac-arnault-databricks-13-2.png)](https://postimg.cc/N97TNcZZ)

</p>
</details>

> Dates and Timestamps - returns a variable's average for each year

<details>


```r
val new_df = Date_Time.withColumn("Year", year(Date_Time("Date")))
val df_avg = new_df.groupBy("Year").mean()
df_avg.select($"Year",$"avg(High)").show()
```

<summary>🔵 See in Zeppelin</summary>
<p> 
  
[![isaac-arnault-zeppelin-13-3.png](https://i.postimg.cc/0jpp5YrZ/isaac-arnault-zeppelin-13-3.png)](https://postimg.cc/V0kSDbqb)

</p>
</details>

```r
val new_df = Date_Time.withColumn("Year", year(Date_Time("Date")))
val df_avg = new_df.groupBy("Year").mean()
df_avg.select($"Year",$"avg(High)").show()
```

<details>
<summary>🔴 See in Databricks</summary>
<p> 
  
[![isaac-arnault-databricks-13-3.png](https://i.postimg.cc/XqMf0HNp/isaac-arnault-databricks-13-3.png)](https://postimg.cc/4757619g)

</p>
</details>

  > Dates and Timestamps - returns a variable Min and Max for each year

<details>


```r
val new_df = Date_Time.withColumn("Year", year(Date_Time("Date")))
val df_min = new_df.groupBy("Year").min()
val df_max = new_df.groupBy("Year").max()

df_min.select($"Year",$"min(Volume)").show()
df_max.select($"Year",$"max(Volume)").show()
```

<summary>🔵 See in Zeppelin</summary>
<p>
  
[![isaac-arnault-zeppelin-13-4.png](https://i.postimg.cc/L87h7q8s/isaac-arnault-zeppelin-13-4.png)](https://postimg.cc/dh2qZVdM)

</p>
</details>

<details>
<summary>🔴 See in Databricks</summary>
<p>
    
[![isaac-arnault-databricks-13-4.png](https://i.postimg.cc/fb9khwVf/isaac-arnault-databricks-13-4.png)](https://postimg.cc/94ccdHtD)

</p>
</details>
