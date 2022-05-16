# Integration

## Parameters

### path_name

the exposed endpoint for the integration. Integrations are called from `{host}/execute/{path_name}`

### description

a documentation field providing an overview of the integrations functions.

### run_async

a boolean flag on whether to run the integration synchronously. Ideal for longer running tasks.

### before_hook

a block of code that executes prior to the initializaion of the integration.

### finally_hook

a block of code that executes prior to the completion of an integration. This block will always run regardless of integration status.

### on_failure_hook

`code` runs after a failed integration but prior to the finally hook.

### on_success_hook

`code` runs after a successful integration but prior to the finally hook.

### http_api

a boolean flag for whether this integration should be exposed as an api endpoint. This allows for integrations to be called from `{glyue_host}/execute/{path_name}`
