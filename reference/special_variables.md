<!-- markdownlint-disable no-inline-html -->

# Special Variables

## retval

Special variable indicating the specified return value from a formula block.

Example:

```py
apply_exchange_rate_adjustments(sf_collateral.response.payload.collateral)
apply_inflation_adjustments(sf_collateral.response.payload.collateral)
retvalue = sum(c.Amount__c for c in sf_collateral.response.payload.collateral)
```

## run_history_id

`run_history_id -> int | None`

Contains the ID of the particular IntegrationRunHistory model that has been generated for the given integration run.  This value can be useful for reporting and analytics purposes.  Please note the value might be None if integration run history persistence is disabled in the integration’s configuration.

## __adapter_config__

Exposes a adapter config field to be overridden via Glyue Field Mappings. Override values will temporarily be used in place of the adapter config value for the Service Request.

> Warning: values stored within the Glyue Field Mapping do not have the same encryption methods employed for the admin usage of adapter configs. Protect your secret keys!

Example

<table>
<thead>
<tr>
<td>FIELD
<td>VALUE
<tbody>
<tr>
<td>__adapter_config__.username
<td>test_user_not_secret
</table>

## output

parameters:

- status: `Any`
- payload: `Any`
- headers: `dict`

payload defaults:

- default success: `Integration {path_name} completed successfully`
- default failure: Error

## input

parameters:

- payload: `Any`
Input payloads are derived from the http request body or can explicitly set in hooks. Usage with callint has the user provide a payload to use for the integration.

## Iterables within integrations: {xx}item and {xx}idx

Each of the components below exposes a field to provide pass an iterable to the component. See the examples for each.

<table>
<thead>
<tr>
<th>Builder Component
<th>Field
<th>Item
<th>Index
<tbody>
<tr>
<td>Service Request
<td>

[call_for_each](../reference/integration_components/servicerequest.md#callforeach-code)

</td>
<td>sritem
<td>sridx
<tr>
<td>Field Mapping
<td>

[include_for_each](../reference/integration_components/fieldmapping.md#includeforeach-code)

</td>
<td>fitem
<td>fidx
<tr>
<td>Validation Rule
<td>

[apply_to_each](../reference/integration_components/validationrule.md#applyif-code---boolean)

</td>
<td>vritem
<td>vridx
<tr>
<td>Mask
<td>

[apply_to_each](../reference/integration_components/mask.md#applytoeach-code)

</td>
<td>mitem
<td>midx
</table>
