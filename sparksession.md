# SparkSession
### SparkSession introduced in version 2.0, is an entry point to underlying PySpark functionality in order to programmatically create PySpark RDD, DataFrame.
```
#Code to create spark session
import pyspark
from pyspark.sql import SparkSession
spark = SparkSession.builder.master("local[1]") \
.appName('myapp.com') \
.getOrCreate()
```
It’s object spark is default available in pyspark-shell and it can be created programmatically using SparkSession

**Spark Session available APIs in different contexts –**

<ul>Spark Context</ul>
<ul>SQL Context</ul>
<ul>Streaming Context</ul>
<ul>Hive Context</ul>

You can create as many SparkSession objects you want using either **SparkSession.builder** or **SparkSession.newSession**.

**SparkSession Commonly Used Methods**
<table>
  <tr>
    <td>version()</td>
    <td>Returns Spark version where your application is running, probably the Spark version you cluster is configured with.</td>
  </tr>
  <tr>
    <td>createDataFrame()</td>
    <td>This creates a DataFrame from a collection and an RDD.</td>
  </tr>
  <tr>
    <td>getActiveSession()</td>
    <td>returns an active Spark session.</td>
  </tr>
  <tr>
    <td>read()</td>
    <td>Returns an instance of DataFrameReader class, this is used to read records from csv, parquet, avro and more file formats into DataFrame.</td>
  </tr>
  <tr>
    <td>readStream()</td>
    <td>Returns an instance of DataStreamReader class, this is used to read streaming data. that can be used to read streaming data into DataFrame.</td>
  </tr>
  <tr>
    <td>sparkContext()</td>
    <td>Returns a SparkContext.</td>
  </tr>
  <tr>
    <td>sql()</td>
    <td>Returns a DataFrame after executing the SQL mentioned.</td>
  </tr>
  <tr>
    <td>sqlContext()</td>
    <td>Returns SQLContext.</td>
  </tr>
  <tr>
    <td>stop()</td>
    <td>Stop the current SparkContext.</td>
  </tr>
  <tr>
    <td>table()</td>
    <td>Returns a DataFrame of a table or view.</td>
  </tr>
  <tr>
    <td>udf()</td>
    <td>Creates a PySpark UDF to use it on DataFrame, Dataset, and SQL.</td>
  </tr>
</table>
    


