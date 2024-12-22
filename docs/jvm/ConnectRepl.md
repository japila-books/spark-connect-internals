---
title: ConnectRepl
---

# ConnectRepl &mdash; Spark Connect REPL

`ConnectRepl` is a standalone application that [can be launched on command line](#main) using the following shell scripts:

* `bin/spark-connect-shell`
* `connector/connect/bin/spark-connect-scala-client`

`ConnectRepl` uses [Ammonite REPL](https://ammonite.io/) for REPL experience.

## Launching Application { #main }

```scala
main(
  args: Array[String]): Unit
```

`main` runs a new [Spark Connect Server](SparkSession.md#withLocalConnectServer) to connect locally.

`main` [builds a SparkConnectClient](../client/SparkConnectClient.md#build).

`main` builds a `SparkSession` for the `SparkConnectClient`.
