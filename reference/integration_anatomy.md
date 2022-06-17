# Integration Anatomy

## Purpose

This is a detailed guide to the anatomical parts of Glyue integrations.

## Integration Components

Integrations provide the wrapper for a set of composable logic with which to connect external systems.

## Integrations

### `Input`: Request body provided to the integration

Inputs can be mutated in the `before_hook` to perform validation, apply Value Mapping Sets or other functionality to facilitate the integration.

### `Output`: Integration response

Integration outputs can be mutated throughout the life of the integration.

> Integration outputs are often overwritten within calls to the service request. The `on_success_hook`, `on_failure_hook`, and the `finally_hook` are the most appropriate places to update the output.

Integration outputs are useful for error handling as well as returning specific payloads or status to calling systems.&#x20;

Asynchronous integrations are a unique case and return an output immediately marking the start of the integration process. Outputs to corresponding systems must be handled explicitly during the integration in these processes.



#### State

Integrations have a success / failure state. The control of this state is flexible and can be triggered at will throughout the life of the integration using the special function [end](special\_functions.md#end). Both service requests and validation rules contain the ability to set the integration into a failure state.&#x20;

## Service Requests

The building blocks of an integration. Service requests are fired off in order to perform operations with connected systems. Each service is associated with an adapter creating a call to the service using the provided adapter configs. Services include external API calls and internal file transformations.

* `Adapter Request` the prepared request. It is available within the integration from the Service Request's `{formula_variable}.request`.
* `Adapter Response` the adapter system response. It is available within the integration from the Service Request's `{formula_variable}.response`.
* `Adapter Success` the state of the adapter service call.
* `Adapter Messages` Optional message component of the adapter. This field is generally used for return adapter specific error messages.

## Field Mappings

Field mappings define the structure of the service request. Adapters generally have a few required field mappings such as `service_path` and `method`.

Field mappings contain the ability to be applied multiple times via an iterable provided to `include_for_each`. This exposes the following variables to be used within the field mapping code blocks.

* fidx: index of the field mapping iterable
* fitem: value of the field mapping iterable

Example:

| include\_for\_each | Value | Field                     |
| ------------------ | ----- | ------------------------- |
| \["test", "test2"] | fitem | fm\_body\[fidx].test\_key |

Generates the following request payload

```py
payload: {
    fm_body: [
        {test_key: "test"},
        {test_key: "test2"}
    ]
}
```

## Value Mapping Sets

Value Mapping Sets are a collection of Value Mappings. These are tied to an integration and can be accessed anywhere within the integration via the [`map_value`](special\_functions.md#mapvalue) special function.

## Value Mappings

Value mappings mutate outgoing request values from one type to another. Common use cases are for assigning statuses from a numeric value to a string representation.

Example

* 0: "Closed"
* 1: "Open"

## Validation Rules

Validation Rules runs validation for input and response data. If a response or requested input payload fails to pass the validation rule, the integration can be put into a failure state or have other logic run.

## Masks

To hide sensitive information throughout the life of the integration. These are applied to either integration inputs or service request responses. Masked information will be replaced with the following "XXXXXXXXXXXX".

## Run History Item

Marks a step within an integration. Each service request or historize statement will generate a Run History Item.
