---
title: 'Spark UDF Using BERT For Encoding Text In Scale'
date: 2020-02-01
permalink: /posts/2020/02/SparkUDF/
tags:
  - Spark
  - Distrbuted System
  - BERT
---

Spark provides a range of built-in solutions for complex issues, yet there are scenarios where its native capabilities fall short. To address this, Spark lets us create and register our own custom functions, known as User-Defined Functions or UDFs.

Spark SQL offers a built-in method to easily register UDFs by passing in a function in your programming language. Scala and Python can use native function and lambda syntax, but in Java we need to extend the UDF class.

UDFs can work on a variety of types and can return a different type than the one they are initially called with. In Python and Java, we need to specify the return type.

Through the use of UDFs, we can encapsulate our functions and apply them to our data at scale.

In this [code](https://colab.research.google.com/drive/11pq1m0oxQZJh2EPhYwax4bLKbriK05Uv?usp=sharing) you can find a few different senarious with UDF implimentation.

  * PySpark UDF with Lambda
  * PySpark UDF using annotations
  * PySpark UDF with BERT
  * PySpark UDF vs Panda UDF

For more information about the pandas_udf you can check this [link](https://www.databricks.com/blog/2017/10/30/introducing-vectorized-udfs-for-pyspark.html)









 
