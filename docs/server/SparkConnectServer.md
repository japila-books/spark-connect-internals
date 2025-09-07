---
title: SparkConnectServer
---

# SparkConnectServer &mdash; Spark Connect Server Standalone Application

`SparkConnectServer` is a standalone application to [start a Spark Connect server](#main) from command line.

`SparkConnectServer` can be started using `sbin/start-connect-server.sh` shell script.

`SparkConnectServer` can be stopped using `sbin/stop-connect-server.sh` shell script.

## Launching Application { #main }

```scala
main(
  args: Array[String]): Unit
```

`main` prints out the following INFO message to the logs:

```text
Starting Spark session.
```

`main` creates a `SparkSession` with the following config options:

Config | Value
-|-
 [spark.sql.artifact.isolation.enabled]({{ book.spark_sql }}/configuration-properties/#spark.sql.artifact.isolation.enabled) | `true`
 [spark.sql.artifact.isolation.alwaysApplyClassloader]({{ book.spark_sql }}/configuration-properties/#spark.sql.artifact.isolation.alwaysApplyClassloader) | `true`

`main` [starts a SparkConnectService](SparkConnectService.md#start).

`main` prints out the following INFO message to the logs:

```text
Spark Connect server started at: [host]:[port]
```

In the end, `main` is paused until the [SparkConnectService](SparkConnectService.md#server) is terminated.
