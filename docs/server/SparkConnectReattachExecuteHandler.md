# SparkConnectReattachExecuteHandler

`SparkConnectReattachExecuteHandler` is used by [SparkConnectService](SparkConnectService.md) to [reattachExecute](SparkConnectService.md#reattachExecute).

## Creating Instance

`SparkConnectReattachExecuteHandler` takes the following to be created:

* <span id="responseObserver"> `StreamObserver[proto.ExecutePlanResponse]`

`SparkConnectReattachExecuteHandler` is created when:

* `SparkConnectService` is requested to [reattachExecute](SparkConnectService.md#reattachExecute)

## Handle ReattachExecuteRequest { #handle }

```scala
handle(
  v: proto.ReattachExecuteRequest): Unit
```

`handle`...FIXME

---

`handle` is used when:

* `SparkConnectService` is requested to [reattachExecute](SparkConnectService.md#reattachExecute)
