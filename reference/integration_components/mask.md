# Mask

## Parameters

### integration

<mark style="color:blue;">`relationship`</mark> <mark style="color:blue;"></mark><mark style="color:blue;"></mark> - <mark style="color:red;">`required`</mark>

Integration to apply the mask to.

### servicerequest

<mark style="color:blue;">`relationship`</mark> <mark style="color:blue;"></mark><mark style="color:blue;"></mark> - <mark style="color:orange;">`optional`</mark>&#x20;

Service request to apply the mask to. Only used for types of `Response`.

### sequence

<mark style="color:yellow;">`integer`</mark> - <mark style="color:red;">`required`</mark>

Order in which to apply the masks for a given input or response.

### type

<mark style="color:yellow;">`string`</mark> - <mark style="color:red;">`required`</mark>

\[`Input`, `Response`] - Specifies which inputs to mask. If type is `Response`, the service request field must be specified.

### field

<mark style="color:red;">`required`</mark>

Field to apply mask to. Field has the current context of the associated input or response.

```py
```

### apply\_if

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:orange;">`optional`</mark>

`code` field that requires a boolean output.

### apply\_to\_each (code)

<mark style="color:yellow;">`iterable`</mark> - <mark style="color:orange;">`optional`</mark>

`code` field that should specify an iterable. `apply_to_each` resolves prior to apply\_if.

### abort\_if\_not\_applied\_x\_times

<mark style="color:yellow;">`integer`</mark> - <mark style="color:red;">`required`</mark>

Forces integration to abort if the mask is not applied at least this many times. If set to 0, this field will be not be applied. By default this is set to zero.

### notes

Documentation field.

### Usage

Masked Parameters hide the incoming response data or input data to prevent sensitive information from being displayed within internal processes.

Example SSN:

|                          |
| ------------------------ |
| 123-45-6789 -> XXXXXXXXX |
