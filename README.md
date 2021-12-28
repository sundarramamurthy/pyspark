# pyspark quick reference
A quick reference guide to the most commonly used patterns and functions in PySpark SQL

### Read CSV file into DataFrame with schema and delimited as comma
```

df = spark.read.option(header='True', inferSchema='True',delimiter=',').csv("/tmp/resources/sales.csv")

```


### Easily reference these as F.my_function() and T.my_type() below
```
from pyspark.sql import functions as F, types as T
```
## Common Operation
```
### Filter on equals condition

df = df.filter(df.is_adult == 'Y')

### Filter on >, <, >=, <= condition

df = df.filter(df.age > 25)

### Sort results

df = df.orderBy(df.age.asc()))  
df = df.orderBy(df.age.desc()))


### Multiple conditions require parentheses around each condition

df = df.filter((df.age > 25) & (df.is_adult == 'Y'))


### Compare against a list of allowed values

df = df.filter(col('age').isin([3, 4, 7]))
```
## Joins
```
### Left join in another dataset

df = df.join(person_lookup_table, 'person_id', 'left')

### Match on different columns in left & right datasets
df = df.join(other_table, df.id == other_table.person_id, 'left')

### Match on multiple columns
df = df.join(other_table, ['first_name', 'last_name'], 'left')

### Useful for one-liner lookup code joins if you have a bunch
def lookup_and_replace(df1, df2, df1_key, df2_key, df2_value):
    return (
        df1
        .join(df2[[df2_key, df2_value]], df1[df1_key] == df2[df2_key], 'left')
        .withColumn(df1_key, F.coalesce(F.col(df2_value), F.col(df1_key)))
        .drop(df2_key)
        .drop(df2_value)
    )

df = lookup_and_replace(people, pay_codes, id, pay_code_id, pay_code_desc)
```

## Column Operations
```
# Add a new static column
df = df.withColumn('status', F.lit('PASS'))

# Construct a new dynamic column
df = df.withColumn('full_name', F.when(
    (df.fname.isNotNull() & df.lname.isNotNull()), F.concat(df.fname, df.lname)
).otherwise(F.lit('N/A'))

# Pick which columns to keep, optionally rename some
df = df.select(
    'name',
    'age',
    F.col('dob').alias('date_of_birth'),
)

# Remove columns
df = df.drop('mod_dt', 'mod_username')

# Rename a column
df = df.withColumnRenamed('dob', 'date_of_birth')

# Keep all the columns which also occur in another dataset
df = df.select(*(F.col(c) for c in df2.columns))

# Batch Rename/Clean Columns
for col in df.columns:
    df = df.withColumnRenamed(col, col.lower().replace(' ', '_').replace('-', '_'))
```




