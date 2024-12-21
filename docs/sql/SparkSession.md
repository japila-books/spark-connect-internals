# SparkSession

`SparkSession` is the entry point to Spark SQL.

## Session UUID { #sessionUUID }

```scala
sessionUUID: String
```

`SparkSession` generates a random UUID when [created](#creating-instance).

`sessionUUID` is used when:

* `SparkConnectPlanner` is requested to [transformCachedLocalRelation](../server/SparkConnectPlanner.md#transformCachedLocalRelation)
* `SessionHolder` is requested to `serverSessionId`
* `SparkConnectArtifactStatusesHandler` is requested to `cacheExists`
* `SparkConnectSessionManager` is requested to [getIsolatedSession](../server/SparkConnectSessionManager.md#getIsolatedSession), [getOrCreateIsolatedSession](../server/SparkConnectSessionManager.md#getOrCreateIsolatedSession)
* `SparkSession` is requested to [addTag](#addTag), [sessionJobTag](#sessionJobTag)
* `ArtifactManager` is requested to _many things_
* `ExecutionListenerBus` is created (one per `SparkSession`) and requested to `doPostEvent`

## sessionJobTag { #sessionJobTag }

```scala
sessionJobTag: String
```

`sessionJobTag` is the following text (with this [sessionUUID](#sessionUUID)):

```text
spark-session-$sessionUUID
```

---

`sessionJobTag` is used when:

* `SparkSession` is requested to [interruptAll](#interruptAll)
* `SQLExecution` is requested for the [executionIdJobTag](SQLExecution.md#executionIdJobTag) and to [withSessionTagsApplied](SQLExecution.md#withSessionTagsApplied)

## interruptOperation { #interruptOperation }

```scala
interruptOperation(
  operationId: String): Seq[String]
```

!!! note "Public API"
    `interruptAll` is part of the public API.

`interruptOperation`...FIXME

## interruptAll { #interruptAll }

```scala
interruptAll(): Seq[String]
```

!!! note "Public API"
    `interruptAll` is part of the public API.

`interruptAll` [doInterruptTag](#doInterruptTag) with this [sessionJobTag](#sessionJobTag) and the following reason:

```text
as part of cancellation of all jobs
```
