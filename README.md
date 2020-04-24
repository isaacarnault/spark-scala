[![1-fg-Hs-M19o-Tdmv-FWEKu-Zl5-HQ.png](https://i.postimg.cc/wTsJDnHL/1-fg-Hs-M19o-Tdmv-FWEKu-Zl5-HQ.png)](https://postimg.cc/SJkJhTnx)

# Data engineering using Spark-Scala - Hands-on
### Tools used: Databricks, Zeppelin • Programming langages: Scala, Spark SQL

[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
The following gist is intended for Data Engineers. It focuses on `Spark` and `Scala`programming.<br>
If we want to handle `batch` and `real-time` data processing, this gist is definitely worth looking into.<br>
We'll learn how to install and use `Spark` and `Scala` on a `Linux` system.<br>
We'll learn the latest `Spark 2.0` methods and updates to the `MLlib` library working with `Spark SQL` and Dataframes.
Please fork it if you find it relevant for your educational or professional path.

### How is gist is structured
This gist is structured into 2 parts.<br>

#### Part 1. Installation of JVM, Spark, Scala on a Linux OS
Related section: SCALA_SPARK_INSTALL

#### Part 2. Spark-Scala programing using Atom, Databricks, Zeppelin

Related sections: SPARK_SCALA_Programming, SPARK_SCALA_entry
SPARK_SCALA_intermediary
  
### Notes related to Spark and Scala

#### Spark
`Spark` is one of the most powerful `Big Data` tools.<br>
`Spark` runs programs up to 100x faster than Hadoop's `MapReduce`.<br>
`Spark` can use data stored in `Cassandra`, Amazon `S3`, Hadoop's`HDFS`, etc.<br>
`MapReduce` requires files to be stored in `HDFS`, `Spark` does not.<br>
`Spark` performs 100x faster than `Mapreduce` because it writes jobs in-memory. `Mapreduce` writes jobs on disk.

<b>Data processing</b><br>
`MapReduce` (Hadoop) writes most data to <b>disk</b> after each `Map` and `Reduce` operation.<br>
`Spark` keeps most of the data <b>in memory</b> after each transformation.<br>
At the core of `Spark` there are `Resilient Distributed Datasets` also known as `RDDs`.<br>
An `RDD` has 4 main features:<br>

1. Distributed collection of data
2. Fault-tolerant
3. Parallel operations which are partitioned
4. An RDD can use many data sources

`RDDs` are immutable, cacheable and lazily evaluated.
There are 2 types of `RDD` operations:<br>
  
  1. Transformations: recipes to follow
  2. Actions: performs recipe's instructions and returns a result
  
  <b>Environment options for `Scala` and `Spark`</b>
  
  1. Text editors, such as `Sublime Text` and `Atom`
  2. IDEs (Integrated Development Environments), such as `IntelliJ` and `Eclipse`
  3. Notebooks, such as `Jupyter`, `Zeppelin` and `Databricks`

#### Scala
`Scala` is a general purpose programming language.<br>
`Scala` was designed by Martin Odersky (Ecole Polytechnique Fédérale de Lausanne).<br>
`Scala` source code is intended to be compiled to `Java` bytecode to run on a `Java Virtual Machine` (JVM).<br>
`Java` librairies can be used directly in `Scala`.<br>

#### Knowledge base

I've uploaded a `.zip` which contains useful slides `MachineLearning`, `Spark` and `Scala`.<br>

#### Storing

For storing datasets and granting access to them, I've used `AWS`.

## Author

* **Isaac Arnault** - AWS Cloud series - Related tags: #EC2 #TLS #AWSCLI #Linux
