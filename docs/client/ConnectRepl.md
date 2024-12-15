---
title: ConnectRepl
---

# ConnectRepl &mdash; Spark Connect Client in Scala

`ConnectRepl` is a reference implementation of [Spark Connect Client](index.md) in Scala.

`ConnectRepl` is a standalone application that [can be launched on command line](#main) using the following shell scripts:

* `bin/spark-connect-shell`
* `connector/connect/bin/spark-connect-scala-client`

`ConnectRepl` uses [Ammonite REPL](https://ammonite.io/) for REPL experience.

## Launching Application { #main }

```scala
main
```

`main` runs a Spark Connect Server ([Spark SQL]({{ book.spark_sql }}/SparkSession/#withLocalConnectServer)).

`main` [builds a SparkConnectClient](SparkConnectClient.md#build).

`main` builds a `SparkSession` for the `SparkConnectClient`.
