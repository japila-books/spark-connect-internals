# ExecuteGrpcResponseSender

## Creating Instance

`ExecuteGrpcResponseSender` takes the following to be created:

* <span id="executeHolder"> [ExecuteHolder](ExecuteHolder.md)
* <span id="grpcObserver"> `StreamObserver[T]`

`ExecuteGrpcResponseSender` is created when:

* `SparkConnectExecutePlanHandler` is requested to [handle a ExecutePlanRequest](SparkConnectExecutePlanHandler.md#handle)
* `SparkConnectReattachExecuteHandler` is requested handle a `ReattachExecuteRequest`

## Run { #run }

```scala
run(
  lastConsumedStreamIndex: Long): Unit
```

`run`...FIXME

---

`run` is used when:

* `ExecuteHolder` is requested to [runGrpcResponseSender](ExecuteHolder.md#runGrpcResponseSender)

### Execute { #execute }

```scala
execute(
  lastConsumedStreamIndex: Long): Unit
```

`execute`...FIXME

### enqueueProgressMessage { #enqueueProgressMessage }

```scala
enqueueProgressMessage(
  force: Boolean = false): Unit
```

`enqueueProgressMessage`...FIXME
