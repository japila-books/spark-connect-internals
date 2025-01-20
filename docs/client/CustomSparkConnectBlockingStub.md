# CustomSparkConnectBlockingStub

## Creating Instance

`CustomSparkConnectBlockingStub` takes the following to be created:

* <span id="channel"> `ManagedChannel`
* <span id="stubState"> `SparkConnectStubState`

`CustomSparkConnectBlockingStub` is created along with [SparkConnectClient](SparkConnectClient.md#bstub).

## executePlanReattachable { #executePlanReattachable }

```scala
executePlanReattachable(
  request: ExecutePlanRequest): CloseableIterator[ExecutePlanResponse]
```

`executePlanReattachable`...FIXME

---

`executePlanReattachable` is used when:

* `SparkConnectClient` is requested to [execute a plan](SparkConnectClient.md#execute) (with [useReattachableExecute](Configuration.md#useReattachableExecute) enabled)
