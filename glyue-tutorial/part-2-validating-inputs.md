# Part 2: Validating Inputs

Now that we have a simple integration that transforms an integration from an input into another structure. Lets add some additional complexity in the logic as well as some basic value mutations.

## Adding business logic in the service request hooks

### Conditionally running the service

Going to the service request table, unhide the columns call\_for\_each and call\_if for the `msg_twice_echo` service request. Here the secondary service request will be called multiple times based on the prior field mapping for `data` in the echo\_msg service request.

| call\_if                | call\_for\_each                 |
| ----------------------- | ------------------------------- |
| isinstance(sritem, str) | echo\_msg.response.payload.data |

To confirm the input values, place some logging statements using the `debug` or `info` special functions. In the `before_prepare_request_hook` for `msg_twice_echo` place the following code snippet.

```py
debug(echo_msg.response.payload, label="echo_msg Response Payload")
```

To test the newly added logic, run the integration again with a string as an input. On the run history page, there should be a single service request for the `echo_msg` and three service requests for the `msg_twice_echo` service request.



## Masking

Sensitive information may be used within the integration. Masking provides a way to hide sensitive information away from users, while still enabling its use.

Navigate to the Mask table. Create a new mask with the following:

| Integration         | Sequence | Type  | Field | Abort if not Applied X Times |
| ------------------- | -------- | ----- | ----- | ---------------------------- |
| echo\_send\_message | 10       | INPUT | data  | 1                            |

Ensure that the `service_request` column is left empty. This mask will convert the field specified based on the `input.payload` of the integration. The integration will be put into a failure state if the mask quantity does not match the specified `abort_if_not_applied.`

Run the integration again with the payload:

```
{"data": "some text"}
```

On the run history page, the `input.payload.data` should now appear as "XXXXXXXXXXXX", but the echo output still works!

## Using Validation Rules

Currently the integration runs on whatever input is provided. It would be convenient to conditionally fail integrations based on the input itself. As an example, we will only accept values which contain the text "sample". This is easily accomplished with Validation Rules.

The code to check for the text:

| Integration     | Sequence | Type  | Field | Rule         | Apply If | Abort on Failure |
| --------------- | -------- | ----- | ----- | ------------ | -------- | ---------------- |
| echo\_send\_msg | 10       | INPUT | data  | "text" in \_ |          |                  |

Refer to [validationrule.md](../reference/integration\_components/validationrule.md "mention") for the importance of \_ and the scope that validation rules run within.

Now when we run the integration with a input that does not contain the string "text" the integration will be put into a failure state. The next section will cover how to handle these types of errors.
