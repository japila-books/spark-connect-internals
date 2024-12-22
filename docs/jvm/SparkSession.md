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

## withLocalConnectServer { #withLocalConnectServer }

```scala
withLocalConnectServer[T](
  f: => T): T
```

`withLocalConnectServer`...FIXME

---

`withLocalConnectServer` is used when:

* `SparkSession.Builder` is requested to [create a SparkSession](SparkSession.Builder.md#create) and [getOrCreate](SparkSession.Builder.md#getOrCreate)
* [ConnectRepl](ConnectRepl.md) standalone application is launched
