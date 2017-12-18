#### Read a csv, with a first line header definition, nullable column values, and inferred schame. Result is a dataframe
val parsed = spark.read.option("header","true").option("nullValue","?").option("inferSchema","true").csv("file_or_directory")

#### View the schema of dataframe
parsed.printSchema()

#### Cache the dataframe to avoid reading from disk again and again
parsed.cache

#### Read a file containing 1 or more json objects per line
val df = spark.read.json("file_or_directory")

#### Create a table view called "linkage" to run sql queries against
parsed.createOrReplaceTempView("linkage")

#### Run a sql query on a table view
spark.sql("SELECT is_match, COUNT(*) cnt FROM linkage GROUP BY is_match ORDER BY cnt DESC").show

#### Show count, min, max, mean, stddev of a dataframe
parsed.describe().show()
