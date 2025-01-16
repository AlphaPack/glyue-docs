# end

`end(payload: any, status: any, headers: dict) -> None`&#x20;

Terminates the currently running integration at the end of the hook in which it is called, logging a failure with the provided status. Integration output is set to the provided payload, status, and headers.

{% hint style="info" %}
If you need the integration to halt at an exact point within a hook, consider throwing an `Exception` within the hook, then performing necessary handling in the [On Failure Hooks](../integration-lifecycle.md#integration-lifecycle).
{% endhint %}

Can be used when some condition requires an integration to terminate early, or at the end of the integration to write custom values to an integration's `output` .&#x20;

```python
try:
    a={"item": True}
    a.item
except KeyError as e:
    end(payload=e, status=500)
```

