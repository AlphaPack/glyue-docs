# Admin Components

## Integration Configs

Provides integration control for emailing on integration runs, storing payload for use with the run history page.

## Integration Permissions

User permissioning must be set per integration. Options are `read`, `write`, `execute`, and `debug`.

## Adapters

Adapter configurations securely store credentials for use with service requests. Please see associated adapter documentation for the correct fields to use.

## Adapter Config Bindings

This is where you specify the relationship between the integration and adapter configuration. Integrations will use the provided adapter config to make service request calls. This configuration can be overridden within integrations with special variable [__adapter_config__](./special_variables.md#adapterconfig)
