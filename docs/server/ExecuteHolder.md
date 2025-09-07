# ExecuteHolder

## Creating Instance

`ExecuteHolder` takes the following to be created:

* <span id="request"> `ExecutePlanRequest`
* <span id="sessionHolder"> `SessionHolder`

`ExecuteHolder` is created when:

* `SparkConnectExecutionManager` is requested to [create an ExecuteHolder](SparkConnectExecutionManager.md#createExecuteHolder)

### ExecuteThreadRunner { #runner }

`ExecuteHolder` creates an [ExecuteThreadRunner](ExecuteThreadRunner.md) when [created](#creating-instance) (with a reference to itself).

The `ExecuteThreadRunner` is used for the following:

* [close](#close)
* [interrupt](#interrupt)
* [isOrphan](#isOrphan)
* [start](#start)

## Start { #start }

```scala
start(): Unit
```

`start` requests this [ExecuteThreadRunner](#runner) to [start](ExecuteThreadRunner.md#start).

---

`start` is used when:

* `SparkConnectExecutionManager` is requested to [createExecuteHolderAndAttach](SparkConnectExecutionManager.md#createExecuteHolderAndAttach)

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
