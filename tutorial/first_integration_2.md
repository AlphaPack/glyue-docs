# Mapping Values & Validating Inputs

Now that we have a basic integration that takes input from one service and calls another service, lets add some additional complexity in the logic as well as some basic value mutations.

## Adding business logic in the service request hooks

### Conditionally running the service

Going to the service request for `salesforce`, double-click on the cell for `after_request_execute_hook`. We will use this hook to filter specific values to be used for the twilio service call.

```py
historize(sw_re.response.payload, label="Salesforce Response Payload")
filtered_response = [ salesforce_person for salesforce_person in sw_re.response.payload if salesforce_person.]  

```

## Inserting Value Mappings

## Using Validation Rules

## Masking Inputs


