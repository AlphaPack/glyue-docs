# Mask

## Parameters

### integration

 Integration to apply the mask to.

### servicerequest

 `optional` Service request to apply the mask to. Only used for types of `Response`.

### sequence

 Order in which to apply the masks for a given input or response.

### type

 [`Input`, `Response`] - Specifies which inputs to mask. If type is `Response`, the service request field must be specified.

### field

 Field to apply mask to. Field inheriets from input or response.

 ```py

 ```

### apply_if

 `code` field that requires a boolean output.

### apply_to_each (code)

 `code` field that should specify an iterable. `apply_to_each` resolves prior to apply_if.

### abort_if_not_applied_x_times

Forces integration to abort if the mask is not applied at least this many times. If set to 0, this field will be a no-op.

### notes

Documentation field.

## Usage

Masked Parameters encrypt the incoming response data or input data to prevent sensitive information from being present to all internal processes.

Common use case example SSN:

<!-- markdownlint-disable no-inline-html -->
<table>
<thead>
<tr>
<th>
<tbody>
<tr>
<td>
</table>
