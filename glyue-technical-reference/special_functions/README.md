# Special Functions

Special functions are globally available functions available throughout the life of an integration.

##



## create\_file\_lock

`create_file_lock(lock_id, timeout: int) -> FileLock`

Please refer to the python package [filelock](https://py-filelock.readthedocs.io/en/latest/index.html) for more information regarding FileLock. Lock\_id is the reference path to the file desired to create a lock on.

```python
create_file_lock('my_file')
```



## calladapter

`calladapter(system: str, service_name: str, label: str, payload: Any, sub_requests: Any) -> AdapterResponse`&#x20;

Makes a call to a configured adapter from within the current integration process.

```python
x = calladapter("ECHO", "N/A", label="Internal adapter call", payload="x")

if x.response.success == True:
    historize("call_successful")
```

## import\_helper

Imports the specified helper function. Please see the Helper Functions for further information on the specific helpers. This imports the helper function to the namespace for the integration, allowing access to the helper in every subsequent hook.

```python
import_helper("ncino")
ncino.autobooking.fire_callback()
```



## list\_files

`list_files() -> List[str]`

Returns a `list` of `str` GlyueFile names for the currently running [Broken link](broken-reference "mention").&#x20;

<pre class="language-python"><code class="lang-python">filenames = list_files()
debug(filenames, "available files")
<strong>
</strong><strong># can write to GlyueFiles
</strong><strong>for name in filenames:
</strong>    with open_glyuefile(name, "a") as file:
        file.write("new line\n")
</code></pre>

##
