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




