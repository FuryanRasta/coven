# Service

Service module allows you to define, bind, invoke services on the COVEN Hub. [Read more about iService](../features/service.md).

## 可用命令

| Name                                                    | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------------ |
| [define](#coven-tx-service-define)                       | Define a new service                                               |
| [definition](#coven-query-service-definition)            | Query a service definition                                         |
| [bind](#coven-tx-service-bind)                           | Bind a service                                                     |
| [binding](#coven-query-service-binding)                  | Query a service binding                                            |
| [bindings](#coven-query-service-bindings)                | Query all bindings of a service definition                         |
| [set-withdraw-addr](#coven-tx-service-set-withdraw-addr) | Set a withdrawal address for a provider                            |
| [withdraw-addr](#coven-query-service-withdraw-addr)      | Query the withdrawal address of a provider                         |
| [update-binding](#coven-tx-service-update-binding)       | Update an existing service binding                                 |
| [disable](#coven-tx-service-disable)                     | Disable an available service binding                               |
| [enable](#coven-tx-service-enable)                       | Enable an unavailable service binding                              |
| [refund-deposit](#coven-tx-service-refund-deposit)       | Refund all deposit from a service binding                          |
| [call](#coven-tx-service-call)                           | Initiate a service call                                            |
| [request](#coven-query-service-request)                  | Query a request by the request ID                                  |
| [requests](#coven-query-service-requests)                | Query active requests by the service binding or request context ID |
| [respond](#coven-tx-service-respond)                     | Respond to a service request                                       |
| [response](#coven-query-service-response)                | Query a response by the request ID                                 |
| [responses](#coven-query-service-responses)              | Query active responses by the request context ID and batch counter |
| [request-context](#coven-query-service-request-context)  | Query a request context                                            |
| [update](#coven-tx-service-update)                       | Update a request context                                           |
| [pause](#coven-tx-service-pause)                         | Pause a running request context                                    |
| [start](#coven-tx-service-start)                         | Start a paused request context                                     |
| [kill](#coven-tx-service-kill)                           | Terminate a request context                                        |
| [fees](#coven-query-service-fees)                        | Query the earned fees of a provider                                |
| [withdraw-fees](#coven-tx-service-withdraw-fees)         | Withdraw the earned fees of a provider                             |
| [schema](#coven-query-service-schema)                    | Query the system schema by the schema name                         |
| [params](#coven-query-service-params)                    | Query values set as service parameters.                            |

## coven tx service define

Define a new service.

```bash
coven tx service define [flags]
```

**Flags:**

| Name, shorthand      | Default | Description                                       | Required |
| -------------------- | ------- | ------------------------------------------------- | -------- |
| --name               |         | Service name                                      | Yes      |
| --description        |         | Service description                               |          |
| --author-description |         | Service author description                        |          |
| --tags               |         | Service tags                                      |          |
| --schemas            |         | Content or file path of service interface schemas | Yes      |

### define a service

```bash
coven tx service define \
    --name=<service name> \
    --description=<service description> \
    --author-description=<author description>
    --tags=tag1,tag2 \
    --schemas=<schemas content or path/to/schemas.json> \
    --chain-id=coven \
    --from=<key-name> \
    --fees=0.3coven
```

### Schemas content example

```json
{
    "input": {
        "$schema": "http://json-schema.org/draft-04/schema#",
        "title": "BioIdentify service input body",
        "description": "BioIdentify service input body specification",
        "type": "object",
        "properties": {
            "id": {
                "description": "id",
                "type": "string"
            },
            "name": {
                "description": "name",
                "type": "string"
            },
            "data": {
                "description": "data",
                "type": "string"
            }
        },
        "required": [
            "id",
            "data"
        ]
    },
    "output": {
        "$schema": "http://json-schema.org/draft-04/schema#",
        "title": "BioIdentify service output body",
        "description": "BioIdentify service output body specification",
        "type": "object",
        "properties": {
            "data": {
                "description": "result data",
                "type": "string"
            }
        },
        "required": [
            "data"
        ]
    }
}
```

## coven query service definition

Query a service definition.

```bash
coven query service definition [service-name] [flags]
```

### Query a service definition

Query the detailed info of the service definition with the specified service name.

```bash
coven query service definition <service name>
```

## coven tx service bind

Bind a service.

```bash
coven tx service bind [flags]
```

**Flags:**

| Name, shorthand | Default | Description                                                                                                                   | Required |
| --------------- | ------- | ----------------------------------------------------------------------------------------------------------------------------- | -------- |
| --service-name  |         | Service name                                                                                                                  | Yes      |
| --deposit       |         | Deposit of the binding                                                                                                        | Yes      |
| --pricing       |         | Pricing content or file path, which is an instance of [Covenhub Service Pricing JSON Schema](../features/service-pricing.json) | Yes      |
| --qos           |         | Minimum response time                                                                                                         | Yes      |
| --options       |         | Non-functional requirements options                                                                                           | Yes      |
| --provider      |         | Provider address, default to the owner                                                                                        |          |

### Bind an existing service definition

The deposit needs to satisfy the minimum deposit requirement, which is the maximal one between `price` * `MinDepositMultiple` and `MinDeposit` (`MinDepositMultiple` and `MinDeposit` are the system parameters, which can be modified through the governance).

```bash
coven tx service bind \
    --service-name=<service name> \
    --deposit=10000coven \
    --pricing=<pricing content or path/to/pricing.json> \
    --qos=50 \
    --options=<non-functional requirements options content or path/to/options.json> \
    --chain-id=coven \
    --from=<key-name> \
    --fees=0.3coven
```

### Pricing content example

```json
{
    "price": "1coven"
}
```

## coven query service binding

Query a service binding.

```bash
coven query service binding <service name> <provider>
```

## coven query service bindings

Query all bindings of a service definition.

```bash
coven query service bindings [service-name] [flags]
```

### Query service binding list

```bash
coven query service bindings <service name> <owner address>
```

## coven tx service update-binding

Update a service binding.

```bash
coven tx service update-binding [service-name] [provider-address] [flags]
```

**Flags:**

| Name, shorthand | Default | Description                                                                                                                                       | Required |
| --------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| --deposit       |         | Deposit added for the binding, not updated if empty                                                                                               |          |
| --pricing       |         | Pricing content or file path, which is an instance of [Covenhub Service Pricing JSON Schema](../features/service-pricing.md), not updated if empty |          |
| --qos           |         | Minimum response time, not updated if set to 0                                                                                                    |          |
| --options       |         | Non-functional requirements options                                                                                                               |          |

### Update an existing service binding

The following example updates the service binding with the additional 10 COVEN deposit

```bash
coven tx service update-binding <service-name> <provider-address> \
    --deposit=10coven \
    --options=<non-functional requirements options content or path/to/options.json> \
    --pricing='{"price":"1coven"}' \
    --qos=50 \
    --chain-id=<chain-id> \
    --from=<key name> \
    --fees=0.3coven
```

## coven tx service set-withdraw-addr

Set a withdrawal address for a provider.

```bash
coven tx service set-withdraw-addr [withdrawal-address] [flags]
```

## coven query service withdraw-addr

Query the withdrawal address of a provider.

```bash
coven query service withdraw-addr [provider] [flags]
```

## coven tx service disable

Disable an available service binding.

```bash
coven tx service disable [service-name] [provider-address] [flags]
```

## coven tx service enable

Enable an unavailable service binding.

```bash
coven tx service enable [service-name] [provider-address] [flags]
```

**Flags:**

| Name, shorthand | Default | Description                            | Required |
| --------------- | ------- | -------------------------------------- | -------- |
| --deposit       |         | deposit added for enabling the binding |          |

### Enable an unavailable service binding

The following example enables an unavailable service binding with the additional 10 COVEN deposit.

```bash
coven tx service enable <service name> <provider-address> --chain-id=coven --from=<key-name> --fees=0.3coven --deposit=10coven
```

## coven tx service refund-deposit

Refund all deposits from a service binding.

```bash
coven tx service refund-deposit [service-name] [provider-address] [flags]
```

### Refund all deposits from an unavailable service binding

Before refunding, you should [disable](#coven-tx-service-disable) the service binding first.

```bash
coven tx service refund-deposit <service name> <provider-address> --chain-id=coven --from=<key-name> --fees=0.3coven
```

## coven tx service call

Initiate a service call.

```bash
coven tx service call [flags]
```

**Flags:**

| Name, shorthand   | Default | Description                                                                                                            | Required |
| ----------------- | ------- | ---------------------------------------------------------------------------------------------------------------------- | -------- |
| --service-name    |         | Service name                                                                                                           | Yes      |
| --providers       |         | Provider list to request                                                                                               | Yes      |
| --service-fee-cap |         | Maximum service fee to pay for a single request                                                                        | Yes      |
| --data            |         | Content or file path of the request input, which is an Input JSON Schema instance                                      | Yes      |
| --timeout         |         | Request timeout                                                                                                        | Yes      |
| --repeated        | false   | Indicate if the reqeust is repetitive (Temporarily disabled in coven-v1.0.0, will be activated after a few versions) |          |
| --frequency       |         | Request frequency when repeated, default to `timeout`                                                                  |          |
| --total           |         | Request count when repeated, -1 means unlimited                                                                        |          |

### Initiate a service invocation request

```bash
coven tx service call \
    --service-name=<service name> \
    --providers=<provider list> \
    --service-fee-cap=1coven \
    --data=<request input or path/to/input.json> \
    --timeout=100 \
    --repeated \
    --frequency=150 \
    --total=100 \
    --chain-id=coven \
    --from=<key name> \
    --fees=0.3coven
```

### Input example

```json
{
    "header": {
        ...
    },
    "body": {
        "id": "1",
        "name": "mage-war",
        "data": "facedata"
    }
}
```

## coven query service request

Query a request by the request ID.

```bash
coven query service request [request-id] [flags]
```

### Query a service request

```bash
coven query service request <request-id>
```

:::tip
You can retrieve the `request-id` in [Query request_id through rpc interface](#Query request_id through rpc interface) or [coven query service requests](#coven query service requests).
:::

### Query request_id through rpc interface

Query `block_results` according to `block height` through `rpc interface`, find `new_batch_request_provider` in `end_block_events`, decode the result with base64 to get `request_id`.

```bash
curl -X POST -d '{"jsonrpc":"2.0","id":1,"method":"block_results","params":["10604"]}' http://localhost:26657
```

## coven query service requests

Query active requests by the service binding or request context ID.

```bash
coven query service requests [service-name] [provider] | [request-context-id] [batch-counter] [flags]
```

### Query active requests of a service binding

```bash
coven query service requests <service name> <provider>
```

### Query service requests by the request context ID and batch counter

```bash
coven query service requests <request-context-id> <batch-counter>
```

## coven tx service respond

Respond to a service request.

```bash
coven tx service respond [flags]
```

**Flags:**

| Name, shorthand | Default | Description                                                                                                                                | Required |
| --------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------ | -------- |
| --request-id    |         | ID of the request to respond to                                                                                                            | Yes      |
| --result        |         | Content or file path of the response result, which is an instance of [Covenhub Service Result JSON Schema](../features/service-result.json) | Yes      |
| --data          |         | Content or file path of the response output, which is an Output JSON Schema instance                                                       |          |

### Respond to a service request

```bash
coven tx service respond \
    --request-id=<request-id> \
    --result=<response result or path/to/result.json> \
    --data=<response output or path/to/output.json>
    --chain-id=coven \
    --from=<key-name> \
    --fees=0.3coven
```

:::tip
You can retrieve the `request-id` in [Query request_id through rpc interface](#Query request_id through rpc interface) or [coven query service requests](#coven query service requests).
:::

### Result example

```json
{
    "code": 200,
    "message": ""
}
```

### Output example

```json
{
    "header": {
        ...
    },
    "body": {
        "data": "userdata"
    }
}
```

## coven query service response

Query a service response.

```bash
coven query service response [request-id] [flags]
```

:::tip
You can retrieve the `request-id` in [Query request_id through rpc interface](#Query request_id through rpc interface) or [coven query service requests](#coven query service requests).
:::

## coven query service responses

Query active responses by the request context ID and batch counter.

```bash
coven query service responses [request-context-id] [batch-counter] [flags]
```

### Query responses by the request context ID and batch counter

```bash
coven query service responses <request-context-id> <batch-counter>
```

## coven query service request-context

Query a request context.

```bash
coven query service request-context [request-context-id] [flags]
```

### Query a request context

```bash
coven query service request-context <request-context-id>
```

:::tip
You can retrieve the `request-context-id` in the result of [service call](#coven-tx-service-call)
:::

## coven tx service update

Update a request context.

```bash
coven tx service update [request-context-id] [flags]
```

**Flags:**

| Name, shorthand   | Default | Description                                                           | Required |
| ----------------- | ------- | --------------------------------------------------------------------- | -------- |
| --providers       |         | Provider list to request, not updated if empty                        |          |
| --service-fee-cap |         | Maximum service fee to pay for a single request, not updated if empty |          |
| --timeout         |         | Request timeout, not updated if set to 0                              |          |
| --frequency       |         | Request frequency, not updated if set to 0                            |          |
| --total           |         | Request count, not updated if set to 0                                |          |

### Update a request context

```bash
coven tx service update <request-context-id> \
    --providers=<provider list> \
    --service-fee-cap=1coven \
    --timeout=0 \
    --frequency=150 \
    --total=100 \
    --chain-id=coven \
    --from=<key name> \
    --fees=0.3coven
```

## coven tx service pause

Pause a running request context.

```bash
coven tx service pause [request-context-id] [flags]
```

### Pause a running request context

```bash
coven tx service pause <request-context-id>
```

## coven tx service start

Start a paused request context.

```bash
coven tx service start [request-context-id] [flags]
```

### Start a paused request context

```bash
coven tx service start <request-context-id>
```

## coven tx service kill

Terminate a request context.

```bash
coven tx service kill [request-context-id] [flags]
```

### Kill a request context

```bash
coven tx service kill <request-context-id>
```

## coven query service fees

Query the earned fees of a provider.

```bash
coven query service fees [provider] [flags]
```

## coven tx service withdraw-fees

Withdraw the earned fees of a provider.

```bash
coven tx service withdraw-fees [provider-address] [flags]
```

## coven query service schema

Query the system schema by the schema name, only pricing and result allowed.

```bash
coven query service schema [schema-name] [flags]
```

### Query the service pricing schema

```bash
coven query service schema pricing
```

### Query the response result schema

```bash
coven query service schema result
```

## coven query service params

Query values set as service parameters.

```bash
coven query service params [flags]
```
