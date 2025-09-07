# ExecuteThreadRunner

`ExecuteThreadRunner` is created alongside [ExecuteHolder](ExecuteHolder.md#runner).

## Creating Instance

`ExecuteThreadRunner` takes the following to be created:

* <span id="executeHolder"> `ExecuteHolder`

## Execute { #execute }

```scala
execute(): Unit
```

`execute` [executeInternal](#executeInternal).

In the end, `execute` requests the [ConnectProgressExecutionListener](SparkConnectService.md#executionListener) to [removeJobTag](ConnectProgressExecutionListener.md#removeJobTag) and removes the job tag (associated with the user and session IDs).

---

`execute` is used when:

* `ExecutionThread` is [started](ExecutionThread.md#run)

## executeInternal { #executeInternal }

```scala
executeInternal(): Unit
```

`executeInternal`...FIXME

---

`executeInternal` is used when:

* `ExecuteThreadRunner` is requested to [execute](#execute)

## Handle Plan { #handlePlan }

```scala
handlePlan(
  request: proto.ExecutePlanRequest): Unit
```

`handlePlan`...FIXME

---

`handlePlan` is used when:

* `ExecuteThreadRunner` is requested to [executeInternal](#executeInternal)
