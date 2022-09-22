# Part 3: Adding Error Handling to the integration

Hopefully integrations are always successful. Reality is full of errors, so let's build a way to gracefully handle them.&#x20;

### Integration Level Errors

Integrations can be put into a failure state due to a variety of factors. The prior example of validation failure is one such example. Let's use that to gain familiarity with the `on_failure_hook.`

#### On Failure Hook

Place a debug statement within the On Failure Hook

```
debug(input.payload, label="integration failure: input")
debug(output.status, label="integration status")
```

Now when running an integration with a failed validation, the two debug statements will run. This becomes particularly useful in sending error messages to connected systems regrading the integration run status.

#### Finally Hook

```
debug("finally hook runs everytime", label="finally hook")
```

The finally hook runs on every integration run.

### Service Request Level Errors

Service requests have the ability to set the integration into a failure state based on the Abort on Failure Field.&#x20;
