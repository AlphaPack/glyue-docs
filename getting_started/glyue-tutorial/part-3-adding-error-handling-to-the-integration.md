# Part 3: Adding Error Handling to the integration

Hopefully all of the integration runs are successful. Reality is slightly more difficult, so let's build a way to gracefully handle errors that arise.

### Integration Level Errors

Integrations can be put into a failure state due to a variety of factors. The prior example of validation failure is one such example. Let's use that to gain familiarity with the `on_failure_hook.`

#### On Failure Hook

Place a debug statement within the On Failure Hook

```
debug(input.payload, label="integration failure: input")
debug(output.status, label="integration status")
```

Now when running an integration with a failed validation, the two debug statements will run. These statements can be invaluable in determining where an integration failed.

#### Finally Hook

```
debug("finally hook runs everytime", label="finally hook")
```

The finally hook runs on every integration run.

### Service Request Level Errors

Service requests have the ability to set the integration into a failure state based on the Abort on Failure Field.

It is time to manually put a service request during the request preparation and enter the `after_prepare_request_failure_hook.` This may have already occurred in prior examples if the payload provided failed to include "data", as the field mapping has disabled the field to be empty.

On the service request, set the `abort_after_execute_request_failure` true to set the integration into a failure state when the service request fails. Now if the integration is tested with an invalid payload it will fail and run the integration failure hooks.

To test that the reverse is true, turn OFF the `abort_after_execute_request_failure`. Test the integration again and see what happens.
