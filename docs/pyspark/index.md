# Spark Connect Python Client

**Spark Connect Python Client** is the Python API of Spark Connect Client.

Spark Connect Python Client is in `pyspark.sql.connect` module.

## Demo

Start [Spark Connect Server](../server/index.md).

```bash
./sbin/start-connect-server.sh
```

Monitor the logs.

```bash
tail -f logs/spark-*-org.apache.spark.sql.connect.service.SparkConnectServer-*.local.out
```

Open the web UI (at http://localhost:4040/connect/) to monitor sessions and requests.

Connect to the local Spark Connect Server with PySpark Shell (`pyspark`).

```bash
uv run --with "pyspark-connect==4.0.0.dev2" \
    ./bin/pyspark --remote "sc://localhost:15002"
```

```py
>>> type(spark)
<class 'pyspark.sql.connect.session.SparkSession'>
```

```py
>>> spark.version
'4.0.0-SNAPSHOT'
```

```py
>>> spark.session_id
'06c3b85b-775a-4438-a539-0a8ef301e00c'
```

```py
>>> dir(spark)
['Builder', '__annotations__', '__class__', '__del__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattr__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', '_active_session', '_cache_local_relation', '_client', '_create_remote_dataframe', '_default_session', '_getActiveSessionIfMatches', '_get_default_session', '_inferSchemaFromList', '_lock', '_parse_ddl', '_profiler_collector', '_session_id', '_set_default_and_active_session', '_start_connect_server', '_to_ddl', 'active', 'addArtifact', 'addArtifacts', 'addTag', 'builder', 'catalog', 'clearProgressHandlers', 'clearTags', 'client', 'conf', 'copyFromLocalToFs', 'createDataFrame', 'dataSource', 'getActiveSession', 'getTags', 'interruptAll', 'interruptOperation', 'interruptTag', 'is_stopped', 'profile', 'range', 'read', 'readStream', 'registerProgressHandler', 'release_session_on_close', 'removeProgressHandler', 'removeTag', 'session_id', 'sql', 'stop', 'streams', 'table', 'tvf', 'udf', 'udtf', 'version']
```

```py
>>> spark._client
<pyspark.sql.connect.client.core.SparkConnectClient object at 0x111d6ca90>
```

```py
>>> dir(spark._client)
['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getstate__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', '_analyze', '_analyze_plan_request_with_metadata', '_artifact_manager', '_build_metrics', '_build_observed_metrics', '_builder', '_channel', '_closed', '_config_request_with_metadata', '_create_profile', '_display_server_stack_trace', '_execute', '_execute_and_fetch', '_execute_and_fetch_as_iterator', '_execute_plan_request_with_metadata', '_fetch_enriched_error', '_handle_error', '_handle_rpc_error', '_interrupt_request', '_profiler_collector', '_progress_handlers', '_proto_to_string', '_resources', '_retry_policies', '_retrying', '_server_session_id', '_session_id', '_stub', '_throw_if_invalid_tag', '_truncate', '_use_reattachable_execute', '_user_id', '_verify_response_integrity', 'add_artifacts', 'add_tag', 'cache_artifact', 'clear_progress_handlers', 'clear_tags', 'close', 'config', 'copy_from_local_to_fs', 'disable_reattachable_execute', 'enable_reattachable_execute', 'execute_command', 'execute_command_as_iterator', 'explain_string', 'get_config_dict', 'get_config_with_defaults', 'get_configs', 'get_retry_policies', 'get_tags', 'host', 'interrupt_all', 'interrupt_operation', 'interrupt_tag', 'is_closed', 'register_data_source', 'register_java', 'register_progress_handler', 'register_udf', 'register_udtf', 'release_session', 'remove_progress_handler', 'remove_tag', 'same_semantics', 'schema', 'semantic_hash', 'set_retry_policies', 'thread_local', 'to_pandas', 'to_table', 'to_table_as_iterator', 'token']
```

```py
>>> dir()
['PROGRESS_BAR_ENABLED', 'SPARK_LOG_SCHEMA', 'SQLContext', 'SparkContext', 'SparkSession', '__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', '_pythonstartup', 'atexit', 'builtins', 'is_remote', 'os', 'platform', 'pyspark', 'sc', 'spark', 'sql', 'sys', 'url', 'urlparse', 'val', 'version', 'warnings']
```
