# end

`end(payload: any, status: any, headers: dict) -> None`&#x20;

Terminates the currently running integration at the end of the hook in which it is called, logging a failure with the provided status. Integration output is set to the provided payload, status, and headers.

```python
try:
    a={"item": True}
    a.item
except KeyError as e:
    end(payload=e, status=500)
```

{% hint style="info" %}
If you need the integration to halt at an exact point within a hook, consider throwing an `Exception` within the hook, then performing necessary handling in the [On Failure Hooks](../integration-lifecycle.md#integration-lifecycle).
{% endhint %}

