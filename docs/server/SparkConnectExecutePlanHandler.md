# SparkConnectExecutePlanHandler

`SparkConnectExecutePlanHandler` is used by [SparkConnectService](SparkConnectService.md) to [executePlan](SparkConnectService.md#executePlan).

## Creating Instance

`SparkConnectExecutePlanHandler` takes the following to be created:

* <span id="responseObserver"> `StreamObserver[proto.ExecutePlanResponse]`

`SparkConnectExecutePlanHandler` is created when:

* `SparkConnectService` is requested to [executePlan](SparkConnectService.md#executePlan)

## Handle ExecutePlanRequest { #handle }

```scala
handle(
  v: proto.ExecutePlanRequest): Unit
```

`handle`...FIXME

---

`handle` is used when:

* `SparkConnectService` is requested to [executePlan](SparkConnectService.md#executePlan)
