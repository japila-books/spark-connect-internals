# ExecutePlanResponseReattachableIterator

## Creating Instance

`ExecutePlanResponseReattachableIterator` takes the following to be created:

* <span id="request"> `proto.ExecutePlanRequest`
* <span id="channel"> `ManagedChannel`
* <span id="retryHandler"> `GrpcRetryHandler`

`ExecutePlanResponseReattachableIterator` is created when:

* `CustomSparkConnectBlockingStub` is requested to [executePlanReattachable](CustomSparkConnectBlockingStub.md#executePlanReattachable)
