---
title: SparkSession
---

# SparkSession &mdash; Spark Connect Scala Client

`SparkSession` is a Spark Connect Scala Client.

`SparkSession` is a `api.SparkSession`.

??? note "Spark SQL's SparkSession"
    There is the [Spark SQL](../sql/SparkSession.md) variant of `api.SparkSession`.

## Creating Instance

`SparkSession` takes the following to be created:

* <span id="client"> [SparkConnectClient](../client/SparkConnectClient.md)
* <span id="planIdGenerator"> Plan ID Generator (`AtomicLong`)

`SparkSession` is created when:

* `SparkSession` utility is used to [create a SparkSession](#create) (for a [Configuration](../client/Configuration.md))
* `SparkSession.Builder` is requested to [tryCreateSessionFromClient](SparkSession.Builder.md#tryCreateSessionFromClient)

## Create SparkSession { #create }

```scala
create(
  configuration: Configuration): SparkSession
```

`create` creates a new [SparkSession](#creating-instance) for a [SparkConnectClient](../client/Configuration.md#toSparkConnectClient) (based on the given [Configuration](../client/Configuration.md)) and this [Plan ID Generator](#planIdGenerator).

---

`create` is used when:

* `SparkSession` utility is used to [load a SparkSession from a cache](#sessions)
* `SparkSession.Builder` is requested to [create a SparkSession](SparkSession.Builder.md#create)

## Execute Command { #execute }

```scala
execute(
  command: proto.Command): Seq[ExecutePlanResponse]
```

!!! note "DeveloperApi"
    `execute` is a `DeveloperApi`.

`execute` [executeInternal](#executeInternal) a new `proto.Plan` for the given `proto.Command`.

---

`execute` is used when:

* `Dataset` is requested to [checkpoint](Dataset.md#checkpoint) and [createTempView](Dataset.md#createTempView)
* `SparkSession` is requested to [registerUdf](#registerUdf)
* `DataFrameWriterImpl` is requested to [executeWriteOperation](DataFrameWriterImpl.md#executeWriteOperation)
* `DataFrameWriterV2Impl` is requested to [executeWriteOperation](DataFrameWriterV2Impl.md#executeWriteOperation)
* `MergeIntoWriterImpl` is requested to [merge](MergeIntoWriterImpl.md#merge)
* `SessionCleaner` is requested to [doCleanupCachedRemoteRelation](SessionCleaner.md#doCleanupCachedRemoteRelation)
* `DataStreamWriter` is requested to [start](DataStreamWriter.md#start)
* `RemoteStreamingQuery` is requested to [executeQueryCmd](RemoteStreamingQuery.md#executeQueryCmd)
* `StreamingQueryListenerBus` is requested to `remove` a `StreamingQueryListener`
* `StreamingQueryManager` is requested to `executeManagerCmd`

### executeInternal { #executeInternal }

```scala
executeInternal(
  plan: proto.Plan): CloseableIterator[ExecutePlanResponse]
```

`executeInternal` requests the [SparkConnectClient](#client) to [execute](../client/SparkConnectClient.md#execute) the given `proto.Plan`.

With an `ExecutePlanResponse`, `executeInternal` [processRegisteredObservedMetrics](#processRegisteredObservedMetrics).

## Run Local Connect Server to Execute Code { #withLocalConnectServer }

```scala
withLocalConnectServer[T](
  f: => T): T
```

`withLocalConnectServer` finds the Spark remote URL based on the following:

1. `spark.remote` in the [sparkOptions](#sparkOptions)
1. `spark.remote` in the system properties (`-D`)
1. `SPARK_REMOTE` environment variable

`withLocalConnectServer` makes sure that the following are all met before starting up a new Spark Connect server:

* The [server](#server) process has not been assigned yet
* The Spark remote URL starts with `local`
* `SPARK_HOME` environment variable is defined and is a directory with `sbin/start-connect-server.sh` shell script

`withLocalConnectServer` starts a new Spark Connect server with the following command:

```text
$SPARK_HOME/sbin/start-connect-server.sh --master [localURL] [sparkOptions]
```

In the end, `withLocalConnectServer` executes the given `f` block.

---

`withLocalConnectServer` is used when:

* `SparkSession.Builder` is requested to [create a SparkSession](SparkSession.Builder.md#create) and [getOrCreate](SparkSession.Builder.md#getOrCreate)
* [ConnectRepl](ConnectRepl.md) standalone application is launched
