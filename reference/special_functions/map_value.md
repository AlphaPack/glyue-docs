# map\_value

`map_value(valuemappingset_name: str, value:Any) -> str`&#x20;

Applies a Value Mapping Set to a provided value. This performs the same operation as when the Value Mapping column is specified on a field mapping.&#x20;

When possible, the Value Mapping column should be used instead of `map_value`within an integration hook.

{% hint style="warning" %}
The value mapping set must be connected to the current integration.
{% endhint %}

```python
#
# Assuming the following exist:
#
# valuemappingset: 'SAMPLEVMS'
# valuemapping:
#     From: 'Testing inputs'
#     To: 'new output'

input.payload.test = 'Testing inputs'
map_value('SAMPLEVMS', input.payload.test)
```
