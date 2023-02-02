# Integration

## Parameters

### path\_name

<mark style="color:yellow;">`string`</mark> - <mark style="color:red;">`required`</mark>

the exposed endpoint for the integration. Integrations are called from `{host}/execute/{path_name}`

### description

Documentation field providing an overview of the integrations functions.

### run\_async

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Boolean flag on whether to run the integration synchronously. Ideal for longer running tasks or in combintaion with `callint` to spawn additional processes.

### before\_hook

A block of code that executes prior to the initializaion of the integration.

### finally\_hook

A block of code that executes prior to the completion of an integration. This block will always run regardless of integration status.

### on\_failure\_hook

`code block` that runs after a failed integration but prior to the finally hook.

### on\_success\_hook

`code block` that runs after a successful integration but prior to the finally hook.

### http\_api

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

A Boolean flag for whether this integration should be exposed. This allows for integrations to be called from `{glyue_host}/integrations/execute/{path_name}`

### Swagger

Glyue has an integrated swagger page to allow for easy endpoint execution from within Glyue. The swagger request and response fields allow for the specification of swagger request bodies and sample responses. These must be formatted in line with the [OpenAPI Specification](https://spec.openapis.org/oas/v3.1.0). Swagger

#### swagger\_request

[Swagger Request Body](https://swagger.io/docs/specification/describing-request-body/) - This field is scoped to the `requestBody` of the OAS 3 specification

```python
{ "content": {
    "application/json": {
        "schema": {
            "type": "string", 
            "example": "sample string input" 
            } 
        } 
    } 
}
```

#### swagger\_response

The input is scoped to the `responses` on the OAS 3 specification.

```python
{ "200": {
     "description": "Sample Response", 
     "content": { 
           "application/json": { 
                "schema": {
                     "type": "string", 
                     "example": 
                     "Example Object" 
                     }
                }
           }
      } 
}
```
