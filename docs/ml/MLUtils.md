# MLUtils

## load { #load }

```scala
load(
  sessionHolder: SessionHolder,
  className: String,
  path: String): Object
```

`load` [replaces the Spark ML operator](#replaceOperator) (`className`).

`load`...FIXME

---

`load` is used when:

* FIXME

## Replace Spark ML Operator { #replaceOperator }

```scala
replaceOperator(
  sessionHolder: SessionHolder,
  name: String): String
```

`replaceOperator`...FIXME

---

`replaceOperator` is used when:

* `MLUtils` is requested to [getEstimator](#getEstimator), [getEvaluator](#getEvaluator), [getTransformer](#getTransformer), [load](#load)
