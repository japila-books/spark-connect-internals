# SparkConnectPlanner

## Creating Instance

`SparkConnectPlanner` takes the following to be created:

* <span id="sessionHolder"> [SessionHolder](SessionHolder.md)

`SparkConnectPlanner` is created when:

* `ExecuteThreadRunner` is requested to [handle a command](ExecuteThreadRunner.md#handleCommand)
* `SparkConnectPlanExecution` is requested to [handle a plan](SparkConnectPlanExecution.md#handlePlan)
* `SparkConnectAnalyzeHandler` is requested to [process an analyze plan request](SparkConnectAnalyzeHandler.md#process)

## transformRelation { #transformRelation }

```scala
transformRelation(
  rel: proto.Relation): LogicalPlan
```

`transformRelation`...FIXME

---

`transformRelation` is used when:

* `SparkConnectPlanExecution` is requested to [handlePlan](SparkConnectPlanExecution.md#handlePlan)
* `SparkConnectPlanner` is requested to _do many things_
* `SparkConnectAnalyzeHandler` is requested to [process a request](SparkConnectAnalyzeHandler.md#process)

### Handle Plugins for Spark Connect Relation Types { #transformRelationPlugin }

```scala
transformRelationPlugin(
  extension: ProtoAny): LogicalPlan
```

`transformRelationPlugin`...FIXME

### transformMapPartitions { #transformMapPartitions }

```scala
transformMapPartitions(
  rel: proto.MapPartitions): LogicalPlan
```

`transformMapPartitions`...FIXME

## transformPythonUDF { #transformPythonUDF }

```scala
transformPythonUDF(
  fun: proto.CommonInlineUserDefinedFunction): PythonUDF
```

`transformPythonUDF` creates a `PythonUDF` (based on the given `fun` and [transformPythonFunction](#transformPythonFunction)).

---

`transformPythonUDF` is used when:

* `SparkConnectPlanner` is requested to [transformMapPartitions](#transformMapPartitions), [transformGroupMap](#transformGroupMap), [transformCoGroupMap](#transformCoGroupMap), [transformCommonInlineUserDefinedFunction](#transformCommonInlineUserDefinedFunction)

## transformPythonFunction { #transformPythonFunction }

```scala
transformPythonFunction(
  fun: proto.PythonUDF): SimplePythonFunction
```

`transformPythonFunction`...FIXME

---

`transformPythonFunction` is used when:

* `SparkConnectPlanner` is requested to [transformPythonUDF](#transformPythonUDF) and [handleRegisterPythonUDF](#handleRegisterPythonUDF)

## Process Command { #process }

```scala
process(
  command: proto.Command,
  responseObserver: StreamObserver[ExecutePlanResponse],
  executeHolder: ExecuteHolder): Unit
```

`process` handles the input `Command` based on its type.

Command Type | Handler
-|-
 `REGISTER_FUNCTION` | [handleRegisterUserDefinedFunction](#handleRegisterUserDefinedFunction)
 `REGISTER_TABLE_FUNCTION` | [handleRegisterUserDefinedTableFunction](#handleRegisterUserDefinedTableFunction)
 `WRITE_OPERATION` | [handleWriteOperation](#handleWriteOperation)
 `CREATE_DATAFRAME_VIEW` | [handleCreateViewCommand](#handleCreateViewCommand)
 `WRITE_OPERATION_V2` | [handleWriteOperationV2](#handleWriteOperationV2)
 `EXTENSION` | [handleCommandPlugin](#handleCommandPlugin)
 `SQL_COMMAND` | [handleSqlCommand](#handleSqlCommand)
 `WRITE_STREAM_OPERATION_START` | [handleWriteStreamOperationStart](#handleWriteStreamOperationStart)
 `STREAMING_QUERY_COMMAND` | [handleStreamingQueryCommand](#handleStreamingQueryCommand)
 `STREAMING_QUERY_MANAGER_COMMAND` | [handleStreamingQueryManagerCommand](#handleStreamingQueryManagerCommand)
 `GET_RESOURCES_COMMAND` | [handleGetResourcesCommand](#handleGetResourcesCommand)

---

`process` is used when:

* `ExecuteThreadRunner` is requested to [handle a command](ExecuteThreadRunner.md#handleCommand)

### handleCommandPlugin { #handleCommandPlugin }

```scala
handleCommandPlugin(
  extension: ProtoAny,
  executeHolder: ExecuteHolder): Unit
```

`handleCommandPlugin`...FIXME
