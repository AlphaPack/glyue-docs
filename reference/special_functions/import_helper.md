# import\_helper

`import_helper(str) -> class`

Imports the specified helper function into the namespace of the integration. The helper can then be accessed in the lifecycle hook where it was imported, as well as every subsequent [lifecycle hook](../integration-lifecycle.md#overview).

```python
import_helper("ncino")
ncino.autobooking.fire_callback()
```



The full list of helper classes is:

```
import_helper("ncino")
import_helper("salesforce")
import_helper("connectware")
import_helper("data_utils")
```

