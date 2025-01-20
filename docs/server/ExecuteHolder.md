# ExecuteHolder

## Creating Instance

`ExecuteHolder` takes the following to be created:

* <span id="request"> `ExecutePlanRequest`
* <span id="sessionHolder"> `SessionHolder`

`ExecuteHolder` is created when:

* `SparkConnectExecutionManager` is requested to [create an ExecuteHolder](SparkConnectExecutionManager.md#createExecuteHolder)

## runGrpcResponseSender { #runGrpcResponseSender }

```scala
runGrpcResponseSender(
  responseSender: ExecuteGrpcResponseSender[proto.ExecutePlanResponse]): Unit
runGrpcResponseSender(
  responseSender: ExecuteGrpcResponseSender[proto.ExecutePlanResponse],
  lastConsumedResponseId: String): Unit
```

`runGrpcResponseSender`...FIXME

---

`runGrpcResponseSender` is used when:

* `SparkConnectExecutePlanHandler` is requested to [handle a ExecutePlanRequest](SparkConnectExecutePlanHandler.md#handle)
* `SparkConnectReattachExecuteHandler` is requested to [handle a ReattachExecuteRequest](SparkConnectReattachExecuteHandler.md#handle)
