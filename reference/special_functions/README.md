# Special Functions

Special functions are globally available functions available throughout the life of an integration.

## keep

`keep()` Adds all provided arguments to the current integration namespace. Once kept, they can be accessed from throughout the life of the integration. The keyword given as a variable sets the variable on the integration.

```python
a = ["list", "items"]
keep(a=a)

b, c = [], []
keep(test=b, c=c)

x = {"y": [], "z": []}
keep(**x)
```

## debug

`historize(value: any, label: str, capture_stack_trace: bool) -> None` Creates a `Run History Item` with the specified variable and optional label.

```python
a = ["SAMPLE"]
debug(a, label="keeping the a variable")
```

## callint

`callint(path_name: str, payload: Any) -> Any` Used to call an integration from within the process of the currently running integration. Callint will return the integration output. Asynchronous integrations will run in a separate thread from the currently running integrations.

```python
payload = "input_str"
x = callint("test_integration", payload)
```

## get\_namespace

`get_namespace() -> namespace` Returns the current integration namespace. Useful for debugging purposes.

```python
current_int_namespace = get_namespace()
current_int_namespacepython
```

## end

`end(payload: any, status: any, headers: dict) -> None` Immediately terminates the currently running integration, logging a failure with the provided status. Integration output is set to the provided payload, status, and headers.

```python
try:
    a={"item": True}
    a.item
except KeyError as e:
    end(payload=e, status=500)
```

## create\_file\_lock

`create_file_lock(lock_id, timeout: int) -> FileLock`

Please refer to the python package [filelock](https://py-filelock.readthedocs.io/en/latest/index.html) for more information regarding FileLock. Lock\_id is the reference path to the file desired to create a lock on.

```python
create_file_lock('my_file')
```

## open\_vault

`open_vault(vault_name) -> Vault`

Attempts to open a vault for a given name. See the Vault guide for more information on how to use Vaults within integrations.

## map\_value

`map_value(valuemappingset_name: str, value:Any) -> str` Applies a Value Mapping Set to a provided value. The value mapping set must be connected to the current integration.

```python
# valuemappingset = 'SAMPLEVMS'
# valuemapping:
#     From: 'Testing inputs'
#     To: 'new output'
input.payload.test = 'Testing inputs'
map_value('SAMPLEVMS', input.payload.test)
```

## calladapter

`calladapter(system: str, service_name: str, label: str, payload: Any, sub_requests: Any) -> AdapterResponse` Makes a call to a configured adapter from within the current integration process.

```python
x = calladapter("ECHO", "N/A", label="Internal adapter call", payload="x")

if x.response.success == True:
    historize("call_successful")
```

## import\_helper

imports the specified helper function. Please see the Helper Functions for further information on the specific helpers. This imports the helper function to the namespace for the integration, allowing access to the helper in every subsequent hook.

```python
import_helper("ncino")
ncino.autobooking.fire_callback()
```

## humanize

Attempts to regex match a field name to the `Message Substitution Name` for the a given integration component.

```python
## Field mapping with:
## 'Field' of 'sample.value'
## 'Message Substitution Name' of Sample
k = humanize("sample.value")
debug(k)
# will output 'Sample'
```

## open\_glyuefile

See [#open\_glyuefile](./#open\_glyuefile "mention") for more information.

## list\_files

`list_files() -> List[str]`

returns a `list` of `str` GlyueFile names for the currently running [integration.md](../integration\_components/integration.md "mention").&#x20;

<pre class="language-python"><code class="lang-python">filenames = list_files()
debug(filenames, "available files")
<strong>
</strong><strong># can write to GlyueFiles
</strong><strong>for name in filenames:
</strong>    with open_glyuefile(name, "a") as file:
        file.write("new line\n")
</code></pre>
