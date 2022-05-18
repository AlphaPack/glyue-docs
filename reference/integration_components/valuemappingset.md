# Value Mapping Set

## Parameters

### integration (realtionship)

Integration value mapping set is applied to

### name (string)

Label for the Value Mapping Set

### description (string)

Documentation field used for value mapping description

### case_sensitive (boolean)

If `True` will respect string case, else all passed values will be converted to lower case for processing strings.

### use_default_to_value (boolean)

Flag for if a default value should be used if no value mappings match the [field mapping value](../integration_components/fieldmapping.md#value-code). If set to False and no value mappings match, then the value will not be transformed.

### default_to_value (boolean | string)

If no value mappings match the field provided, this will be the value used for the field.
