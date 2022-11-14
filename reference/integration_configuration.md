# Admin Components

### Global Config

The base configuration for Glyue.

* Email configuration for reports
* Storing of request & response payloads to Glyue

### Integration Configs

Provides control for emails, storing payload for use with the run history page.

Email fields should be comma separated

### Integration Permissions

User permissions must be set per integration. Options are `read`, `write`, `execute`, and `debug`. By default, the user who creates the integration has full integration permissions. Every other user, who is not a designated superuser, will need to have permissions explicitly granted.

### Adapter Configurations

Adapter configurations securely store credentials for use with service requests. Please see associated adapter documentation for the correct fields to use.

### Adapter Configuration Bindings

The relationship between the integration and adapter configuration. Integrations will use the provided adapter config to make any associated service request calls. This configuration can be overridden within integrations with special variable [**adapter\_config**](special\_variables.md#adapterconfig)**.**

### Webservice Endpoints

Integrations can be triggered from their HTTP POST method for the integration `path_name`. This endpoint exposes integrations to be called using all available HTTP verbs.
