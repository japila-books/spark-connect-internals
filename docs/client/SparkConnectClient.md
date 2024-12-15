# SparkConnectClient

## Creating Instance

`SparkConnectClient` takes the following to be created:

* <span id="configuration"> [Configuration](Configuration.md)
* <span id="channel"> `ManagedChannel` ([gRPC]({{ grpc.api }}/io/grpc/ManagedChannel.html))

`SparkConnectClient` is created when:

* `Configuration` is requested for a [SparkConnectClient](Configuration.md#toSparkConnectClient)

## Clone Itself { #copy }

```scala
copy(): SparkConnectClient
```

`copy` requests this [Configuration](#configuration) for a [SparkConnectClient](Configuration.md#toSparkConnectClient)

---

`copy` is used when:

* `SparkSession` ([Spark SQL]({{ book.spark_sql }}/SparkSession/#newSession)) is requested for a new `SparkSession`
