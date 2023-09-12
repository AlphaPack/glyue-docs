# Service Request

## Parameters

### integration

<mark style="color:blue;">`relationship`</mark> - <mark style="color:red;">`required`</mark>

The integration that the service request is realted to.

### parent\_servicerequest

<mark style="color:blue;">`relationship`</mark> - <mark style="color:red;">`required`</mark>

If specified, the service request will be attached to another service request.

### sequence

<mark style="color:yellow;">`integer`</mark> - <mark style="color:red;">`required`</mark>

Order in which the service requests associated with the integration will execute.

### system

<mark style="color:yellow;">`string`</mark> - <mark style="color:red;">`required`</mark>

Adapter to call. Adapter names are specified within adapter documentation.

### service\_name

<mark style="color:yellow;">`string`</mark> - <mark style="color:red;">`required`</mark>

Service name to be used with associated request. Usage is determined by the adapter being called.

### formula\_variable

<mark style="color:yellow;">`string`</mark> - <mark style="color:red;">`required`</mark>

Variable assigned to the service request. Each service request is created within the namespace using this formula variable. If the `call_for_each` field is specified then this value is a list.

### call\_if

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:orange;">`optional`</mark>

Code block to return a boolean value.

### call\_for\_each (code)

<mark style="color:yellow;">`iterable`</mark> - <mark style="color:orange;">`optional`</mark>

Specifies an iterable. Service will run for each item within the iterable. Resolves before the call\_if block.

### message\_substitution\_name

<mark style="color:yellow;">`string`</mark> - <mark style="color:orange;">`optional`</mark>

Replaces the sritem with specified string.

### notes

Documentation field

### Service Request Hooks

These are code blocks that are run during processes of the service request. See the [Integration Life Cycle Diagram](../../media/integration\_life\_cycle.svg) for timing of the hooks.

* before\_prepare\_request\_hook
* after\_prepare\_request\_success\_hook
* after\_prepare\_request\_failure\_hook
* before\_execute\_request\_hook
* after\_execute\_request\_success\_hook
* after\_execute\_request\_failure\_hook
* abort\_after\_execute\_request\_failure
* skip\_execute\_if\_no\_sub\_requests
* after\_overall\_success\_hook
* after\_overall\_failure\_hook

### Attributes

Refer to the [#service-requests](../integration\_anatomy.md#service-requests "mention") for the attributes assigned to a service request upon creation
