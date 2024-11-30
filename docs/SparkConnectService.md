# SparkConnectService

`SparkConnectService` is a `BindableService` ([gRPC]({{ grpc.api }}/io/grpc/BindableService.html)).

`SparkConnectService` can be started as a gRPC service using [startGRPCService](#startGRPCService).

## Creating Instance

`SparkConnectService` takes the following to be created:

* <span id="debug"> `debug` flag

`SparkConnectService` is created when:

* `SparkConnectService` is requested to [startGRPCService](#startGRPCService)

## start

```scala
start(
  sc: SparkContext): Unit
```

`start` [starts the gRPC service](#startGRPCService) and then [creates a listener and the UI](#createListenerAndUI).

---

`start` is used when:

* `SparkConnectPlugin` is requested for the [Spark driver plugin](SparkConnectPlugin.md#driverPlugin)
* [SparkConnectServer](SparkConnectServer.md) standalone application is started

### Start gRPC Service { #startGRPCService }

```scala
startGRPCService(): Unit
```

`startGRPCService` reads the values of the following configuration properties:

Configuration Property | Default Value
-----------------------|--------------
 `spark.connect.grpc.debug.enabled` | `true`
 `spark.connect.grpc.binding.port` | `15002`
 `spark.connect.grpc.maxInboundMessageSize` | `128 * 1024 * 1024`

`startGRPCService` builds a `NettyServerBuilder` with the `spark.connect.grpc.binding.port` and a [SparkConnectService](SparkConnectService.md).

`startGRPCService` [registers interceptors](SparkConnectInterceptorRegistry.md#chainInterceptors).

`startGRPCService` [builds the server](#server) and starts it.

## executePlan { #executePlan }

??? note "gRPC Java"

    ```scala
    executePlan(
      request: proto.ExecutePlanRequest,
      responseObserver: StreamObserver[proto.ExecutePlanResponse]): Unit
    ```

    `executePlan` is part of the `SparkConnectServiceImplBase` abstraction.

`executePlan` creates a [SparkConnectStreamHandler](SparkConnectStreamHandler.md) (with the given `StreamObserver`) to let it [handle the request](SparkConnectStreamHandler.md#handle).
