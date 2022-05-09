# Mask

## Parameters

- integration - parent integration
- servicerequest - parent servicerequest
- sequence - order in which to apply the mask.
- type - [Input, Response]
- field - field to apply mask to.
- apply_if - `code` field that should output a boolean.
- apply_to_each - `code` field that should specify an iterable.
- abort_if_not_applied_x_times
- notes - documentation field

## Usage

Masked Parameters encrypt the incoming response data or input data to prevent sensitive information from being present to internal processes.

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
