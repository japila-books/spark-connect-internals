# SparkSession

`SparkSession` is the entry point to Spark SQL.

## Session UUID { #sessionUUID }

```scala
sessionUUID: String
```

`SparkSession` generates a random UUID when [created](#creating-instance).

`sessionUUID` is used when:

* `SparkConnectPlanner` is requested to [transformCachedLocalRelation](./server/SparkConnectPlanner.md#transformCachedLocalRelation)
* `SessionHolder` is requested to `serverSessionId`
* `SparkConnectArtifactStatusesHandler` is requested to `cacheExists`
* `SparkConnectSessionManager` is requested to [getIsolatedSession](./server/SparkConnectSessionManager.md#getIsolatedSession), [getOrCreateIsolatedSession](./server/SparkConnectSessionManager.md#getOrCreateIsolatedSession)
* `SparkSession` is requested to [addTag](#addTag), [sessionJobTag](#sessionJobTag)
* `ArtifactManager` is requested to _many things_
* `ExecutionListenerBus` is created (one per `SparkSession`) and requested to `doPostEvent`
