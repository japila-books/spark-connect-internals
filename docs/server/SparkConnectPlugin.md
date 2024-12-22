# SparkConnectPlugin

`SparkConnectPlugin` is a Spark driver plugin that [starts a SparkConnectService](SparkConnectService.md#start) upon initialization.

`SparkConnectPlugin` is a `SparkPlugin` ([Spark Core]({{ book.spark_core }}/plugins/SparkPlugin)) with the [driver-side component](#driverPlugin) only.

`SparkConnectPlugin` can be installed into Spark applications using `spark.plugins` ([Spark Core]({{ book.spark_core }}/configuration-properties/#spark.plugins)) configuration property (e.g., [Spark Connect Shell](../spark-connect-shell.md)).

## Driver-Side Component { #driverPlugin }

??? note "SparkPlugin"

    ```scala
    driverPlugin(): DriverPlugin
    ```

    `driverPlugin` is part of the `SparkPlugin` ([Spark Core]({{ book.spark_core }}/plugins/SparkPlugin/#driverPlugin)) abstraction.

`driverPlugin` creates a new `DriverPlugin` (Apache Spark) that does the following:

* [Starts a SparkConnectService](SparkConnectService.md#start) when requested to initialize
* [Stops the SparkConnectService](SparkConnectService.md#stop) when requested to shut down
