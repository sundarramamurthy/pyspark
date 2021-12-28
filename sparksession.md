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




