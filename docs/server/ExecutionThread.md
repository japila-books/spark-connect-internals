# ExecutionThread

`ExecutionThread` is a thread of execution of [ExecuteThreadRunner](ExecuteThreadRunner.md#execute).

`ExecutionThread` uses the following thread name (with [operationId](ExecuteHolder.md#operationId)):

```text
SparkConnectExecuteThread_opId=[operationId]
```

??? note "Private Inner Class"
    `ExecutionThread` is a private inner class of [ExecuteThreadRunner](ExecuteThreadRunner.md) with full access to the internal state.
