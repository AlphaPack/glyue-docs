# parentint

`Dict`

Gives access to the parent integration's namespace from a child integration during a synchronous [`callint`](../special_functions/callint.md)  integration run. The full set of special variables are available on the parent.

{% hint style="info" %}
Asynchronous integrations have no reference to their parent integrations.
{% endhint %}

```python
# Access the parent's input
parentint.input.payload

# Returns the parent integration's Integration Run History Item
parentint.run_history_id 
```
