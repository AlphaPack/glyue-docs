# sritem/sridx

Provides access to the value (`sritem`) and index (`sridx`) when calling a [service request](../../../glyue-technical-reference/integration_components/servicerequest.md) multiple times using the [`call_for_each`](../../../glyue-technical-reference/integration_components/servicerequest.md#call_for_each) column.

These variables are only populated when the `call_for_each` column is set, and are only accessible in the service request's lifecycle hooks and in all columns on its [field mappings](../../../glyue-technical-reference/integration_components/field-mapping.md). They are usually used to configure field mappings when calling a service request repeatedly.

{% hint style="info" %}
Read more about the `call_for_each` column [here](../../../glyue-technical-reference/integration_components/servicerequest.md#call_for_each).
{% endhint %}

```
# Given
call_for_each = ["abc@email.com", "def@email.com", "ghi@email.com"]

# First iteration
fitem ==> "abc@email.com"
fidx ==> 0

# Second iteration
fitem ==> "def@email.com"
fidx ==> 1

etc...
```



**Example usage**

```
# Given
call_for_each = [
    {"name": "Sally", "email": "sally@email.com"},
    {"name": "Benjamin", "email": "benjamin@email.com"},
    {"name": "David", "email": "david@email.com"}
]

# To send an email to each individual, set the following on the service request's field mapping
field: email_address
value: sritem.email

```

