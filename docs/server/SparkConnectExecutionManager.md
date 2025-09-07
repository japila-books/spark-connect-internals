# SparkConnectExecutionManager

## Creating Instance

`SparkConnectExecutionManager` takes no arguments to be created.

`SparkConnectExecutionManager` is created when:

* `SparkConnectService` is requested for the [executionManager](SparkConnectService.md#executionManager)

## createExecuteHolderAndAttach { #createExecuteHolderAndAttach }

```scala
createExecuteHolderAndAttach(
  executeKey: ExecuteKey,
  request: proto.ExecutePlanRequest,
  sessionHolder: SessionHolder,
  responseObserver: StreamObserver[proto.ExecutePlanResponse]): ExecuteHolder
```

`createExecuteHolderAndAttach`...FIXME

---

`createExecuteHolderAndAttach` is used when:

* `SparkConnectExecutePlanHandler` is requested to [handle a ExecutePlanRequest message](SparkConnectExecutePlanHandler.md#handle)
