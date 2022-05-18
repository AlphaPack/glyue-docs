# Service Request

## Parameters

### integration

The integration that the service request is realted to.

### parent_servicerequest

If speicified, the service request will run underneath the parent.

### sequence (integer)

Order in which the service requests associated with the integration will execute.

### system (string)

Adapter to call. Adapter names are specified within adapter documentation.

### service_name (string)

Service name to be used with associated request. Usage is determined by the adapter being called.

### formula_variable (string)

Variable assigned to the service request. Each service request is created within the namespace using this formula variable. If the `call_for_each` field is specified then this value is a list.

### call_if (code)

Code block to return a boolean value.

### call_for_each (code)

Specifies an iterable. Service will run for each item within the iterable. Resolves before the call_if block.

### service request hooks

These are code blocks that are run during processes of the service request. See the [Integration Life Cycle Diagram](../../media/integration_life_cycle.svg) for timing of the hooks.

- before_prepare_request_hook
- after_prepare_request_success_hook
- after_prepare_request_failure_hook
- before_execute_request_hook
- after_execute_request_success_hook
- after_execute_request_failure_hook
- abort_after_execute_request_failure
- skip_execute_if_no_sub_requests
- after_overall_success_hook
- after_overall_failure_hook

### message_substitution_name (string)

Replaces the sritem with specified string.

### notes

Documentation field
