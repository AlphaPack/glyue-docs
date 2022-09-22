# Part 1: Creating the Integration

This is a walk-through for a basic integration connecting salesforce and twilio to send a notification regarding the status of client. Pieces of the

## Assumptions

* Basic knowledge of reading and understanding json
* Basic knowledge of python
* You have an instance of Glyue accessible with correct credentials.

## Setup

### Salesforce

First we will need to setup a salesforce environment for us to use. Create a new trailhead environment using the following [sign-up](https://trailhead.salesforce.com/en/c/start\_here). Follow the account creation process for salesforce then go to your newly created account's [orgs](https://trailhead.salesforce.com/users/profiles/orgs). It will take some time for the environment to setup.

Once the environment has been created, go to the environment and setup a `connected app` within salesforce.

### Twilio

### Echo

Echo services return whatever input was passed to the service as an output, or creates a new response based on input payloads. Please refer to the echo adapter documentation for more details.

### Glyue

With both of the target development credentials obtained it is now time to enter them into Glyue. Within Glyue, navigate to the validate configs page. Press the validate configs button to check if current configs pass an initial ping with the credentials provided. If your credentials are invalid, go back to the Admin page for your specific adapter and confirm that credentials provided are correct.

### Integration

Navigate to the build page. Add a new row for the integration table. Fill out the `path_name`, and set the `http_api` dropdown to `True`.

| path name           | http\_api | run\_async |
| ------------------- | --------- | ---------- |
| echo\_send\_message | True      | False      |

Save and move on to the next step.

### Service Request

Navigate to the service request table. Create two new rows. Initially hide the following columns using the _column filter_: \[ call\_if, call\_for\_each ]. We will touch more on these later.

| Integration         | Sequence | System | Service Name | Formula Variable | skip\_execute\_if\_no\_sub\_requests |
| ------------------- | -------- | ------ | ------------ | ---------------- | ------------------------------------ |
| echo\_send\_message | 10       | ECHO   | N/A          | msg\_echo        | False                                |
| echo\_send\_message | 20       | ECHO   | N/A          | msg\_twice\_echo | False                                |

formula\_variable is used for both request and response creation. Access to the variable set here is provided within the integration once the service request process starts.

Save and move on to the next step!

### Field Mapping

Navigate to the Field Mapping Builder. Create four new field mappings that we will be linked to the created service requests.&#x20;

| Service Request  | Sequence | Field         | Value                                        | Value Type | Nullable |
| ---------------- | -------- | ------------- | -------------------------------------------- | ---------- | -------- |
| msg\_echo        | 10       | value         | input.payload.data                           | str        | False    |
| msg\_echo        | 20       | nested.value  | input.payload.data                           | str        | False    |
| msg\_echo        | 30       | data          | \[ val for val in \[input.payload.data]\*3 ] | list       | False    |
| msg\_twice\_echo | 10       | result        | msg\_echo.response.payload.value             | str        | False    |
| msg\_twice\_echo | 20       | nested.result | msg\_echo.response.payload.nested.value      | str        | False    |

The values of the `msg_twice_echo` field mappings are dependent upon the results of the `msg_echo` service request. Save your work up to this point.

### Configuration

Time to add configuration for the integration. Navigate to the administration page and click on the Add an Integration Config Button. Select the newly created integration from the drop-down menu. Enable the `Store run history` and `Store payloads in run history`. These settings are required to be able to view the inputs and outputs on the run history page.

### Send Request

Within Glyue, navigate to the SwaggerAPI. This is the easiest way to trigger integrations using Glyue as it will handle all necessary authentication. Open the newly created endpoint and in the input body for the payload put the in the payload as so.

```json
{ "data: "sample_input_text" }
```

Press execute. The response from within the swagger page should show a `Integration Completed Successfully`.

Navigate to the Run-History page. Here you can see the specific steps for the integration. With an Input, both service requests and the Output.

### Alternative: use a REST API client like Insomnia, or Postman

Use basic auth for the authentication. Create a new endpoint.
