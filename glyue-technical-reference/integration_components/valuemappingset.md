# Value Mapping Set

## Parameters

### integration

<mark style="color:blue;">`relationship`</mark> - <mark style="color:red;">`required`</mark>

Integration value mapping set is applied to.

### name

<mark style="color:yellow;">`string`</mark> - <mark style="color:red;">`required`</mark>

Label for the Value Mapping Set

### description

<mark style="color:yellow;">`string`</mark> - <mark style="color:orange;">`optional`</mark>

Documentation field used for value mapping description

### case\_sensitive

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

If `True` will respect string case, else all passed values will be converted to lower case for processing strings.

### use\_default\_to\_value

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Flag for if a default value should be used if no value mappings match the [field mapping value](../../reference/integration\_components/fieldmapping.md#value-code). If set to False and no value mappings match, then the value will not be transformed.

### default\_to\_value (boolean | string)

<mark style="color:yellow;">`boolean | string`</mark> - <mark style="color:red;">`required`</mark>

If no value mappings match the field provided, this will be the value used for the field.
