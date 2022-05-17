# Service Request

## integration

The integration that the service request is realted to.

## parent_servicerequest

If speicified, the service request will run underneath the parent.

## sequence (integer)

Order in which the service requests associated with the integration will execute.

## system (string)

Adapter to call. Adapter names are specified within adapter documentation.

## service_name (string)

Service name to be used

## formula_variable (string)

## call_if (code)

Code block to return a boolean value.

## call_for_each (code)

Specifies an iterable. Service will run for each item within the iterable. Resolves before the call_if block.

## before_prepare_request_hook (code)

Code block that runs prior to sritem.request being created.

## after_prepare_request_success_hook (code)

Code block that runs after sritem.request is created.

## after_prepare_request_failure_hook (code)

## before_execute_request_hook (code)

## after_execute_request_success_hook (code)

## after_execute_request_failure_hook (code)

## abort_after_execute_request_failure (boolean)

## skip_execute_if_no_sub_requests (boolean)

## after_overall_success_hook (code)

## after_overall_failure_hook (code)

## message_substitution_name (string)

Replaces the sritem with specified string.

## notes

Documentation field
