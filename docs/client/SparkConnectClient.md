# SparkConnectClient

## Creating Instance

`SparkConnectClient` takes the following to be created:

* <span id="configuration"> [Configuration](Configuration.md)
* <span id="channel"> `ManagedChannel` ([gRPC]({{ grpc.api }}/io/grpc/ManagedChannel.html))

`SparkConnectClient` is created when:

* `Configuration` is requested for a [SparkConnectClient](Configuration.md#toSparkConnectClient)

## CustomSparkConnectBlockingStub { #bstub }

`SparkConnectClient` creates a new [CustomSparkConnectBlockingStub](CustomSparkConnectBlockingStub.md) when [created](#creating-instance) with the following:

CustomSparkConnectBlockingStub | Value
-|-
[ManagedChannel](CustomSparkConnectBlockingStub.md#channel) | This [ManagedChannel](#channel)
[SparkConnectStubState](CustomSparkConnectBlockingStub.md#stubState) | This [SparkConnectStubState](#stubState)

This `CustomSparkConnectBlockingStub` is used for the following:

* [Analyze a plan](#analyze)
* [Config](#config)
* [Execute a plan](#execute)
* [Interrupt All](#interruptAll)
* [Interrupt Operation](#interruptOperation)
* [Interrupt by Tag](#interruptTag)
* [Release Session](#releaseSession)
* Create this [ArtifactManager](#artifactManager)

## Clone Itself { #copy }

```scala
copy(): SparkConnectClient
```

`copy` requests this [Configuration](#configuration) for a [SparkConnectClient](Configuration.md#toSparkConnectClient)

---

`copy` is used when:

* `SparkSession` ([Spark SQL]({{ book.spark_sql }}/SparkSession/#newSession)) is requested for a new `SparkSession`

## Release Session { #releaseSession }

```scala
releaseSession(): proto.ReleaseSessionResponse
```

`releaseSession` builds a new `ReleaseSessionRequest` with the following:

* This [UserContext](#userContext)
* This [sessionId](#sessionId)
* This [userAgent](#userAgent)

In the end, `releaseSession` requests this [CustomSparkConnectBlockingStub](#bstub) to [releaseSession](CustomSparkConnectBlockingStub.md#releaseSession) with the `ReleaseSessionRequest`.

---

`releaseSession` is used when:

* `SparkSession` is requested to [close](../sql/SparkSession.md#close)

## Execute Plan { #execute }

```scala
execute(
  plan: proto.Plan): CloseableIterator[proto.ExecutePlanResponse]
```

`execute`...FIXME

??? note "Not used"
    `execute` does not seem used.
