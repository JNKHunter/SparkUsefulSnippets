### Read a csv, with a first line header definition, nullable column values, and inferred schame
val parsed = spark.read.option("header","true").option("nullValue","?").option("inferSchema","true").csv("file_or_directory")
