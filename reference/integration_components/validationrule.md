# Validation Rule

## Parameters

### integration (relation)

### servicerequest (relation)

### sequence (integer)

### type (string)

- `INPUT`: applies on the input payload received by the integration
- `RESPONSE`: applies to payload received from adapter
- `REQUEST`: applies to payload sent to adapter

### field (code) -> boolean

`default`: True
Validation rule is assesed on the boolean value returned from `field`.

### rule (code)

### apply_if (code) -> boolean

`default`: True
Will only apply the validation rule if these resolves to True.

### apply_to_each (code) -> iterable

### pass_hook

### fail_hook

### abort_on_failure

### valuemappingset

### valuemappingset_side

### max_length

### message_substitution_name
