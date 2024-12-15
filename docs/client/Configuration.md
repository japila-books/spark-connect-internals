# Configuration

## toSparkConnectClient { #toSparkConnectClient }

```scala
toSparkConnectClient: SparkConnectClient
```

`toSparkConnectClient` creates a new [SparkConnectClient](SparkConnectClient.md) for this `Configuration` and a new [ManagedChannel](#createChannel).

---

`toSparkConnectClient` is used when:

* `SparkSession` ([Spark SQL]({{ book.spark_sql }}/SparkSession/#create)) is requested to create a `SparkSession`
* `SparkConnectClient` is requested to [clone itself](SparkConnectClient.md#copy)
* `SparkConnectClient.Builder` is requested to [build a SparkConnectClient](#build)
