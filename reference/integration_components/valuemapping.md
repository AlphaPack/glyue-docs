# Value Mapping

An easy way to handle cases for transformations of field mappings from one value into another. Takes the computed field mapping value and applies then applies the transformation.

### valuemappingset

<mark style="color:blue;">`relationship`</mark> <mark style="color:blue;"></mark><mark style="color:blue;"></mark> - <mark style="color:red;">`required`</mark>

Value Mapping Set that the Value Mapping belongs to.

### from\_value

<mark style="color:yellow;">`string | bool`</mark> - <mark style="color:red;">`required`</mark>

A string or boolean value. Values passed as inputs to field mappings will undergo be matched against the from\_value.

### to\_value&#x20;

<mark style="color:yellow;">`string | bool`</mark> - <mark style="color:red;">`required`</mark>

An output string or boolean value. The output of the matching `from_value`. This field takes an explicit string and transforms it

### notes

Documentation field

### Examples

