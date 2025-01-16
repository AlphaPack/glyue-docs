# calladapter

`calladapter(system: str, service_name: str, label: str, payload: Any, sub_requests: Any) -> AdapterResponse`&#x20;

Makes a call to a configured adapter from within the current integration process.

```python
x = calladapter("ECHO", "N/A", label="Internal adapter call", payload="x")

if x.response.success == True:
    historize("call_successful")
```
