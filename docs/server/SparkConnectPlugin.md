# SparkConnectPlugin

`SparkConnectPlugin` is a Spark driver plugin (a `SparkPlugin` ([Apache Spark]({{ book.spark_core }}/plugins/SparkPlugin)) with the [driver-side component](#driverPlugin) only).

`SparkConnectPlugin` is the main entry point for Spark Connect in Apache Spark applications.

## Driver-Side Component { #driverPlugin }

??? note "SparkPlugin"

    ```scala
    driverPlugin(): DriverPlugin
    ```

    `driverPlugin` is part of the `SparkPlugin` ([Apache Spark]({{ book.spark_core }}/plugins/SparkPlugin/#driverPlugin)) abstraction.

`driverPlugin` creates a new `DriverPlugin` (Apache Spark) that does the following:

* [Starts a SparkConnectService](SparkConnectService.md#start) when requested to initialize
* [Stops the SparkConnectService](SparkConnectService.md#stop) when requested to shut down
