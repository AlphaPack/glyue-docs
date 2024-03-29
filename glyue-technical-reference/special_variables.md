# Special Variables

### retvalue

Special variable indicating the specified return value from a formula block.

Examples:

```python
apply_exchange_rate_adjustments(sf_collateral.response.payload.collateral)
apply_inflation_adjustments(sf_collateral.response.payload.collateral)
retvalue = sum(c.Amount__c for c in sf_collateral.response.payload.collateral)
```

```python
if input.payload == "test value":
    retvalue = input.payload
```

### run\_history\_id

`run_history_id -> int | None`

Contains the ID of the particular IntegrationRunHistory model that has been generated for the given integration run. This value can be useful for reporting and analytics purposes. Please note the value might be `None` if integration run history persistence is disabled in the integration’s configuration.

### **adapter\_config**

Exposes a adapter config field to be overridden via Glyue Field Mappings. Override values will temporarily be used in place of the adapter config value for the Service Request.

> Warning: values stored within the Glyue Field Mapping do not have the same encryption methods employed for the admin usage of adapter configs. Protect your secret keys!

Example

| FIELD                            | VALUE                   |
| -------------------------------- | ----------------------- |
| \_\_adapter\_config\_\_.username | test\_user\_not\_secret |

### output

parameters:

* status: `Any`
* payload: `Any`
* headers: `dict`

payload defaults:

* default success: `Integration {path_name} completed successfully`
* default failure: Error

### input

parameters:

* payload: `Any` Input payloads are derived from the http request body or can explicitly set in hooks. Usage with callint has the user provide a payload to use for the integration.

### Iterable within integrations: {xx}item and {xx}idx

Each of the components below exposes a field to provide pass an iterable to the component. See the examples for each.

| Builder Component | Field                                                                                                  | Item   | Index |
| ----------------- | ------------------------------------------------------------------------------------------------------ | ------ | ----- |
| Service Request   | [#service-requests](integration\_anatomy.md#service-requests "mention")                                | sritem | sridx |
| Field Mapping     | [#include\_for\_each-code](integration\_components/field-mapping.md#include\_for\_each-code "mention") | fitem  | fidx  |
| Validation Rule   | [#apply\_to\_each](integration\_components/validationrule.md#apply\_to\_each "mention")                | vritem | vridx |
| Mask              | [#apply\_to\_each-code](integration\_components/mask.md#apply\_to\_each-code "mention")                | mitem  | midx  |

### parentint

Gives access to the parent integration's namespace from a child integration during a [Broken link](broken-reference "mention") synchronous integration run. Asynchronous integrations have no reference to their parent integrations.

```python
# will return the parent integration's Integration Run History Item
parentint.run_history_id 
# access to the parent's input
parentint.input.payload
```
