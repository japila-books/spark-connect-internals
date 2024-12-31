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

## Try to Create New Session for SparkConnectClient { #tryCreateSessionFromClient }

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

## Reuse or Create SparkSession { #getOrCreate }

??? note "SparkSessionBuilder"

    ```scala
    getOrCreate(): SparkSession
    ```

    `getOrCreate` is part of the `SparkSessionBuilder` ([Spark SQL]({{ book.spark_sql }}/SparkSessionBuilder.md#getOrCreate)) abstraction.

??? note "Public API"
    `getOrCreate` is part of the public API.

???+ warning "Generative AI"
    This description was co-authored using Generative AI tools, namely [JetBrains AI Assistant](https://www.jetbrains.com/ai/) (with the [openai-gpt-4o](https://openai.com/index/hello-gpt-4o/) model).

    Prompt: "What does getOrCreate do? Please explain every line."

`getOrCreate` either returns an existing `SparkSession` (that matches the configuration provided) or creates a new `SparkSession` instance if no suitable session exists.

`getOrCreate` is used to ensure that a `SparkSession` is always available without having to worry whether a session already exists.

`getOrCreate` uses a caching mechanism alongside proper configuration and session updates.

---

`getOrCreate` [starts a local Spark Connect server](SparkSession.md#withLocalConnectServer) unless already started.

`getOrCreate` [attempts to create a session by directly reusing the current client (if it exists and is valid)](#tryCreateSessionFromClient).
If a valid client exists, a new `SparkSession` is built and returned immediately.

Otherwise (if no valid client exists or the session is not reusable), `getOrCreate` finds the `SparkSession` (in the [sessions](SparkSession.md#sessions) by the [Configuration](#configuration)) or creates a session.

`getOrCreate` updates the global default and/or active `SparkSession` in the application.

`getOrCreate` applies [`spark.sql`-prefixed options](SparkSession.md#sparkOptions) and the builder's options to the new or existing session.
