# Field Mapping

## servicerequest (relation)

The service request the field mapping is related to.

## sequence (integer)

Order in which the field mappings will be processed for the associated service request.

## field (code)

request.payload output value to map to

## value (code)

request.payload input value to map from

## value_type (python type)

Specifies a python type to cast the values.

## target_record_type (string)

Documentation field

## target_field_name (string)

Documentation field

## source_record_type (string)

Documentation field

## source_field_name (string)

Documentation field

## valuemappingset (relation)

Value Mapping Set to apply to the field.

## include_if (code)

Code block to return a boolean value.

## include_for_each (code)

Specifies an iterable. Field mappings will resolve for each item within the iterable. Resolves before the include_if block.

## nullable (boolean)

Specifies whether the field can be nullable. If `True` and the field resovles to null, the integration will fail and be set into an error state.

## message_substitution_name (string)

Replaces the fitem with specified string.
