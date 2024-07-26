Setting up the Apache Spark on Visual Code IDE
----------------------------------------------

1. Create virtual environment (`.venv`) for the project.
2. Install pyspark to the virtual environment using `pip install pyspark`


Reading csv data using spark
----------------------------
```
spark_df = spark.read
            .format("csv")
            .option("header", "true")
            .option("inferSchema, "true")
            .load("/databricks-datasets/learning-spark-v2/sf-fire/sf-fire-calls.csv")
```

Reading csv data using spark csv method
---------------------------------------
```
spark_df = spark.read
            .csv("/databricks-datasets/learning-spark-v2/sf-fire/sf-fire-calls.csv", 
            header="true", 
            inferSchema="true")
```

Creating globalTemporaryView of the dataframe
---------------------------------------------
```
spark_df.createGlobalTempView("fire_service_calls_view")
```

With this view, we can run Sql queries such as
```
select * from global_temp.fire_service_calls_view
```

Creating database
-----------------
```
create database if not exists demo_db
```

Create Table
------------
```
create table if not exists demo_db.fire_service_calls_tbl(
    CallNumber integer,
    UnitID string,
    IncidentNumber integer,
    CallType: string
) using parquet
```

Insering data into table
------------------------
```
insert into demo_db.fire_service_calls_tbl
values(1234, null, null, null)
```

Viewing data from table
-----------------------
```
select * from demo_db.fire_service_calls_tbl
```


