# Integration

## Parameters

### path_name

the exposed endpoint for the integration. Integrations are called from `{host}/execute/{path_name}`

### description

Documentation field providing an overview of the integrations functions.

### run_async

Boolean flag on whether to run the integration synchronously. Ideal for longer running tasks or in combintaion with `callint` to spawn additional processes.

### before_hook

A block of code that executes prior to the initializaion of the integration.

### finally_hook

A block of code that executes prior to the completion of an integration. This block will always run regardless of integration status.

### on_failure_hook

`code` runs after a failed integration but prior to the finally hook.

### on_success_hook

`code` runs after a successful integration but prior to the finally hook.

### http_api

A boolean flag for whether this integration should be exposed as an api endpoint. This allows for integrations to be called from `{glyue_host}/integrations/execute/{path_name}`
