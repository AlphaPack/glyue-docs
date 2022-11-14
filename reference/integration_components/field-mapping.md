# Field Mapping

## Parameters

### servicerequest

<mark style="color:blue;">`relationship`</mark> - <mark style="color:red;">`required`</mark>

The service request that the field mapping belongs to.

### valuemappingset

<mark style="color:blue;">`relationship`</mark> - <mark style="color:orange;">`optional`</mark>

The valuemappingset to apply to the [#value](field-mapping.md#value "mention").

### sequence

<mark style="color:yellow;">`integer`</mark> - <mark style="color:red;">`required`</mark>

Order in which the field mappings associated with the service request will execute.

### field

<mark style="color:yellow;">`string`</mark> - <mark style="color:red;">`required`</mark>

Skeleton for the input payload you want to send as the service request. These correspond to dictionary like keys for Flex objects.

### value

<mark style="color:yellow;">`string`</mark> - <mark style="color:red;">`required`</mark>

Value to applied to the given field value.

### value\_type

<mark style="color:yellow;">`string`</mark> - <mark style="color:red;">`required`</mark>

Typecast to perform on non-null values

### include\_if

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:orange;">`optional`</mark>

Code block to return a boolean value.

### include\_for\_each (Code)

<mark style="color:yellow;">`iterable`</mark> - <mark style="color:orange;">`optional`</mark>

Specifies an iterable. Service will run for each item within the iterable. Resolves before the include\_if block.

### nullable

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Indicator for if the [#value](field-mapping.md#value "mention") can be set to null.

### message\_substitution\_name

<mark style="color:yellow;">`string`</mark> - <mark style="color:orange;">`optional`</mark>

Replaces the sritem with specified string.

### Documentation Fields

* `target_record_type`
* `target_field_name`
* `source_record_type`
* `source_field_name`



## Additional Information:

### value\_type:

The value type field serves dual purposes:

1. Validation
2. Type casting

Consider a fieldmapping where at integration runtime the value evaluates to the string “5.0”:

If the `value_type` is “float” then we convert that value to a float before passing it on.\
If the `value_type` is "dict" then we would raise an exception\
If the `value_type` is "str" then we would pass the value along unmodified.

**Note that the validation functionality is pretty limited** - if your `value_type` was “str” for example just about any value would be converted and not throw an error, even if your value was a float or a dictionary.
