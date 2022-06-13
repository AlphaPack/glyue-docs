# Special Functions

Special functions are globally available functions available throughout the life of an integration.

## keep

`keep()` Adds all provided arguments to the current integration namespace. Once kept, they can be accessed from throughout the life of the integration. The keyword given as a variable sets the variable on the integration.

```py
a = ["list", "items"]
keep(a=a)

b, c = [], []
keep(test=b, c=c)

x = {"y": [], "z": []}
keep(**x)
```

## Historize

`historize(value: any, label: str, capture_stack_trace: bool) -> None` Creates a `Run History Item` with the specified variable and optional label.

```py
a = ["SAMPLE"]
historize(a, label="keeping the a variable")
```

## callint

`callint(path_name: str, payload: Any) -> Any` Used to call an integration from within the process of the currently running integration. Callint will return the integration output. Asynchronous integrations will run in a separate thread from the currently running integrations.

```py
payload = "input_str"
x = callint("test_integration", payload)
```

## get\_namespace

`get_namespace() -> namespace` Returns the current integration namespace. Useful for debugging purposes.

```py
current_int_namespace = get_namespace()
current_int_namespace
```

## end

`end(payload: any, status: any, headers: dict) -> None` Immediately terminates the currently running integration, logging a failure with the provided status. Integration output is set to the provided payload, status, and headers.

```py
try:
    a={"item": True}
    a.item
except KeyError as e:
    end(payload=e, status="KeyError")
```

## create\_file\_lock

## open\_vault

## map\_value

`map_value(valuemappingset_name: str, value:Any) -> str` Applies a Value Mapping Set to a provided value. The value mapping set must be connected to the current integration.

## calladapter

`calladapter(system: str, service_name: str, label: str, payload: Any, sub_requests: Any) -> AdapterResponse` Makes a call to a configured adapter from within the current integration process.

```py
x = calladapter("ECHO", "N/A", label="Internal adapter call", payload="x")

if x.response.success == True:
    historize("call_successful")
```
