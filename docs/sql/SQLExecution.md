# SQLExecution

## executionIdJobTag { #executionIdJobTag }

```scala
executionIdJobTag(
  session: SparkSession,
  id: Long)
```

`executionIdJobTag` is the following text (with the [sessionJobTag](SparkSession.md#sessionJobTag) of the given `SparkSession`):

```text
[sessionJobTag]-execution-root-id-[id]
```

---

`executionIdJobTag` is used when:

* `SparkSession` is requested to [interruptOperation](#interruptOperation)
* `SQLExecution` is requested to [withNewExecutionId0](#withNewExecutionId0)

## withNewExecutionId { #withNewExecutionId }

```scala
withNewExecutionId[T](
  queryExecution: QueryExecution,
  name: Option[String] = None)(
  body: => T): T
```

`withNewExecutionId` [withNewExecutionId0](#withNewExecutionId0) with the given `QueryExecution`, the optional `name` and the `body` (as a `Right` value).

## withNewExecutionIdOnError { #withNewExecutionIdOnError }

```scala
withNewExecutionIdOnError(
  queryExecution: QueryExecution,
  name: Option[String] = None)(
  t: Throwable): Unit
```

`withNewExecutionIdOnError` [withNewExecutionId0](#withNewExecutionId0) with the given `QueryExecution`, the optional `name` and the `Throwable` (as a `Left` value).

---

`withNewExecutionIdOnError` is used when:

* `QueryExecution` is requested to `assertAnalyzed`

## withExecutionId { #withExecutionId }

```scala
withExecutionId[T](
  sparkSession: SparkSession,
  executionId: String)(
  body: => T): T
```

`withExecutionId`...FIXME

---

`withExecutionId` is used when:

* `SubqueryExec` physical operator is requested for the `relationFuture`
* `SubqueryBroadcastExec` physical operator is requested for the `relationFuture`

## withThreadLocalCaptured { #withThreadLocalCaptured }

```scala
withThreadLocalCaptured[T](
  sparkSession: SparkSession,
  exec: ExecutorService)(
  body: => T): Future[T]
```

`withThreadLocalCaptured`...FIXME

---

`withThreadLocalCaptured` is used when:

* `BroadcastExchangeExec` physical operator is requested for the `relationFuture`
* `BroadcastExchangeLike` physical operator is requested for the `triggerFuture`
* `SubqueryExec` physical operator is requested for the `relationFuture`
* `SubqueryBroadcastExec` physical operator is requested for the `relationFuture`
* `ShuffleExchangeLike` physical operator is requested for the `triggerFuture`

## withNewExecutionId0 { #withNewExecutionId0 }

```scala
withNewExecutionId0[T](
  queryExecution: QueryExecution,
  name: Option[String] = None)(
  body: Either[Throwable, () => T]): T
```

`withNewExecutionId0`...FIXME

---

`withNewExecutionId0` is used when:

* `SQLExecution` is requested to [withNewExecutionId](#withNewExecutionId) and [withNewExecutionIdOnError](#withNewExecutionIdOnError)

## withSessionTagsApplied { #withSessionTagsApplied }

```scala
withSessionTagsApplied[T](
  sparkSession: SparkSession)(
  block: => T): T
```

`withSessionTagsApplied`...FIXME

---

`withSessionTagsApplied` is used when:

* `SQLExecution` is requested to [withExecutionId](#withExecutionId), [withNewExecutionId0](#withNewExecutionId0), and [withThreadLocalCaptured](#withThreadLocalCaptured)
