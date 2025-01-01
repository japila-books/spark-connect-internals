# Spark Connect Client's Python API

`pyspark.sql.connect` module is the official Python API of Spark Connect Client.

```bash
uv run --with "pyspark-connect==4.0.0.dev2" \
    ./bin/pyspark --remote "sc://localhost"
```

```py
>>> dir()
['PROGRESS_BAR_ENABLED', 'SPARK_LOG_SCHEMA', 'SQLContext', 'SparkContext', 'SparkSession', '__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', '_pythonstartup', 'atexit', 'builtins', 'is_remote', 'os', 'platform', 'pyspark', 'sc', 'spark', 'sql', 'sys', 'url', 'urlparse', 'val', 'version', 'warnings']
```
