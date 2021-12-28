# pyspark quick reference
A quick reference guide to the most commonly used patterns and functions in PySpark SQL

### Easily reference these as F.my_function() and T.my_type() below
```
from pyspark.sql import functions as F, types as T
```

### Filter on equals condition
```
df = df.filter(df.is_adult == 'Y')
```

### Filter on >, <, >=, <= condition
```
df = df.filter(df.age > 25)
```

### Multiple conditions require parentheses around each condition
```
df = df.filter((df.age > 25) & (df.is_adult == 'Y'))
```

### Compare against a list of allowed values
```
df = df.filter(col('first_name').isin([3, 4, 7]))
```

### Sort results
```
df = df.orderBy(df.age.asc()))  
df = df.orderBy(df.age.desc()))
```


