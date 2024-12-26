---
tags:
  - DeveloperApi
---

# SparkSession.Builder

## Creating Instance

`SparkSession.Builder` takes no arguments to be created.

`SparkSession.Builder` is created using [SparkSession.builder](SparkSession.md#builder) utility.

## Create SparkSession (with Local Spark Connect Server) { #create }

```scala
create(): SparkSession
```

??? note "Public API"
    `create` is part of the public API.

`create` [runs a new Spark Connect Server](SparkSession.md#withLocalConnectServer).

`create` [tries to create a brand new SparkSession from this SparkConnectClient](#tryCreateSessionFromClient) or [creates a brand new SparkSession from scratch](SparkSession.md#create) (for the [Configuration](../client/SparkConnectClient.Builder.md#configuration) of this [SparkConnectClient.Builder](../client/SparkConnectClient.md#builder)).

`create` [setDefaultAndActiveSession](#setDefaultAndActiveSession) and then [applyOptions](#applyOptions).

## Try to Create New Session from SparkConnectClient { #tryCreateSessionFromClient }

```scala
tryCreateSessionFromClient(): Option[SparkSession]
```

!!! note
    `tryCreateSessionFromClient` always returns a brand new [SparkSession](SparkSession.md).

`tryCreateSessionFromClient` creates a new [SparkSession](SparkSession.md) (with this [SparkConnectClient](#client) and the [planIdGenerator](SparkSession.md#planIdGenerator)) when all the following is met:

* This [SparkConnectClient](#client) is available
* The [underlying session is valid](../client/SparkConnectClient.md#isSessionValid)

Otherwise, `tryCreateSessionFromClient` returns no `SparkSession`.

---

`tryCreateSessionFromClient` is used when:

* `SparkSession.Builder` is requested to [create a new SparkSession](#create) and [getOrCreate a SparkSession](#getOrCreate)
