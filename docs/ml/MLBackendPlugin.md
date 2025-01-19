# MLBackendPlugin

`MLBackendPlugin` is an [abstraction](#contract) of [Spark Connect ML backends](#implementations) that can [replace a Spark ML operator with a backend-specific implementation](#transform).

## Contract

### Replace Spark ML Operator { #transform }

```java
Optional<String> transform(
  String mlName)
```

Used when:

* `MLUtils` is requested to [replaceOperator](MLUtils.md#replaceOperator)

## Implementations

!!! note
    No built-in implementations available.
