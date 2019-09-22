A `Spark - Scala` project using `Zeppelin`.

Use <b>Netflix2011_2016.csv</b> file. See <b>datasets.md</b> section of this gist.<br>

We can use the same commands as below in our `Databricks` notebook to see what they return.<br>

Some of them will be performed in `Scala`, others in `Spark SQL`.

<br>

Create a new notebook in `Zeppelin`.<br>
1. Load the dataset, turn it to a dataframe and check the variables

```r
val df = sqlContext.read.format("csv")
  .option("header", "true")
  .option("inferSchema", "true")
  .load("/home/zaki/Desktop/Netflix2011_2016.csv")

df.columns
```
    
<details>
<summary>🔵 See output</summary>
<p> 
    
[![spark-scala-project-1.png](https://i.postimg.cc/TwKTMxCJ/spark-scala-project-1.png)](https://postimg.cc/vgwJfJR4)

  </p>
</details>

2. Print schema of the dataframe

```r
df.printSchema
```
    
<details>
<summary>🔵 See output</summary>
<p> 

[![spark-scala-project-2.png](https://i.postimg.cc/TwBfTssM/spark-scala-project-2.png)](https://postimg.cc/LYkrTxRN)

  </p>
</details>

3. Read the first 5 rows of the dataframe

```r
df.show(5)
```
    
<details>
<summary>🔵 See output</summary>
<p>
    
[![spark-scala-project3.png](https://i.postimg.cc/1X6PXHxg/spark-scala-project3.png)](https://postimg.cc/XBVtD9Y3)

  </p>
</details>

4. Get statistics about the dataframe

```r
val df = sqlContext.read.format("csv")
  .option("header", "true")
  .option("inferSchema", "true")
  .load("/home/zaki/Desktop/Netflix2011_2016.csv")

df.describe().show()
```
    
<details>
<summary>🔵 See output</summary>
<p> 

[![spark-scala-project-4.png](https://i.postimg.cc/mgdxbqcX/spark-scala-project-4.png)](https://postimg.cc/JsBYxp5Z)

  </p>
</details>

5. Get the ratio from two variables ("High", "Volume")

```r
val df2 = df.withColumn("H_V Ratio", df("High")/df("Volume"))
df2.columns
```    

```r
df2.head(1)
```
<details>
<summary>🔵 See output</summary>
<p> 

[![spark-scala-project-5.png](https://i.postimg.cc/sDcqc8Jj/spark-scala-project-5.png)](https://postimg.cc/Whd5p5KC)

  </p>
</details>

6. Check what day has the peak "High" and "Price"

```r
import spark.implicits._
df.orderBy($"High".desc).show(1)
```
    
<details>
<summary>🔵 See output</summary>
<p> 
    
[![spark-scala-project-6.png](https://i.postimg.cc/QCq4f914/spark-scala-project-6.png)](https://postimg.cc/hQf1jGCT)

  </p>
</details>

7. Check what day has the peak "High" and "Price"

```r
df.select(mean("Volume")).show()
```
    
<details>
<summary>🔵 See output</summary>
<p> 
    
[![spark-scala-project-7.png](https://i.postimg.cc/ZKTDCHz1/spark-scala-project-7.png)](https://postimg.cc/yWbTGFdP)

  </p>
</details>

8. Get the Max and Min of a specific variable - Max

```r
df.select(max("Close")).show()
```

```r
df.select(min("Close")).show()
```
   
   <details>
<summary>🔵 See output</summary>
<p>  
    
[![spark-scala-project-8.png](https://i.postimg.cc/0NJVLH7J/spark-scala-project-8.png)](https://postimg.cc/VSm9tgGY)

  </p>
</details>

9. Get the number of days where "Close" was lower than $550

```r
import spark.implicits._
df.filter($"Close"<550).count()
```
    
```r
df.filter("Close < 550").count()
```

<details>
<summary>🔵 See output</summary>
<p> 
    
[![spark-scala-project-9.png](https://i.postimg.cc/pr0Q9DDH/spark-scala-project-9.png)](https://postimg.cc/m1H1J1XX)

  </p>
</details>

10. Get the number of days where "Close" was lower than $550

```r
import spark.implicits._
(df.filter($"High">300).count()*1.0/ df.count() )*100
```
    
<details>
<summary>🔵 See output</summary>
<p> 
    
[![spark-scala-project-10.png](https://i.postimg.cc/J7K5dWS2/spark-scala-project-10.png)](https://postimg.cc/bdDns4yx)

  </p>
</details>

11. Get the Pearson correlation between "Low" and "Close"

```r
df.select(corr("Low","Close")).show()
```

<details>
<summary>🔵 See output</summary>
<p> 

[![spark-scala-project-11.png](https://i.postimg.cc/286FsKD8/spark-scala-project-11.png)](https://postimg.cc/dDbydn3z)

  </p>
</details>

12. Get the max High per Year

```r
import spark.implicits._
val year_df = df.withColumn("Year", year(df("Date")))
val year_max = year_df.select($"Year", $"High").groupBy("Year").max()
year_max.select($"Year",$"max(High)").show()
```
    
<details>
<summary>🔵 See output</summary>
<p> 
    
[![spark-scala-project-12.png](https://i.postimg.cc/25pQBjBV/spark-scala-project-12.png)](https://postimg.cc/rDJ0Bkjk)

  </p>
</details>

13. Getting the average Close price for each Month

```r
import spark.implicits._
val month_df = df.withColumn("Month", month(df("Date")))
val month_avg = month_df.select($"Month", $"Close").groupBy("Month").mean()
month_avg.select($"Month",$"avg(Close)").orderBy("Month").show()
```
    
<details>
<summary>🔵 See output</summary>
<p> 
    
[![spark-scala-project-13.png](https://i.postimg.cc/50gLGwKC/spark-scala-project-13.png)](https://postimg.cc/MMcnfjS6)

  </p>
</details>
