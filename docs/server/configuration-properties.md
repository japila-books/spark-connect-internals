---
title: Configuration Properties
---

# Server's Configuration Properties

## spark.connect.grpc

### <span id="CONNECT_GRPC_BINDING_ADDRESS"> binding.address { #spark.connect.grpc.binding.address }

**spark.connect.grpc.binding.address**

Default: (undefined)

### <span id="CONNECT_GRPC_BINDING_PORT"> binding.port { #spark.connect.grpc.binding.port }

**spark.connect.grpc.binding.port**

Default: `15002`

### debug.enabled { #spark.connect.grpc.debug.enabled }

**spark.connect.grpc.debug.enabled**

Default: `true`

### <span id="CONNECT_GRPC_INTERCEPTOR_CLASSES"> interceptor.classes { #spark.connect.grpc.interceptor.classes }

**spark.connect.grpc.interceptor.classes**

A comma-separated list of class names that must implement the `io.grpc.ServerInterceptor` interface.

Default: (undefined)

### <span id="CONNECT_GRPC_PORT_MAX_RETRIES"> port.maxRetries { #spark.connect.grpc.port.maxRetries }

**spark.connect.grpc.port.maxRetries**

The maximum number of port retry attempts for the gRPC server binding.

Default: `0`
