# Creating your first integration

This is a walk-through for a basic integration connecting salesforce and twilio to send a notification regarding the status of client. Pieces of the

## Assumptions

- Basic knowledge of reading and understanding json
- Basic knowledge of python
- You have an instance of Glyue accessible with correct credentials.

## Setup

### Salesforce

First we will need to setup a salesforce environment for us to use. Create a new trailhead environment using the following [sign-up](https://trailhead.salesforce.com/en/c/start_here). Follow the account creation process for salesforce then go to your newly created account's [orgs](https://trailhead.salesforce.com/users/profiles/orgs). It will take some time for the environemnt to setup.

Once the environment has been created, go to the environment and setup a `connected app` within salesforce.

### Twilio

### Glyue

With both of the target development credentials obtained it is now time to enter them into glyue. Within Glyue, navigate to the validate configs page. Press the validate configs button to check if current configs pass an initial ping with the credentials provided. If your credentials are invalid, go back to the Admin page for your specific adapter and confirm that credentials provided are correct.

### Integration

Navigate to the build page. Add a new row for the integration table. Fill out the `path_name`, and set the `http_api` dropdown to `True`.

<!-- markdownlint-disable no-inline-html -->
<table>
<thead>
<tr>
<th>path name
<th>http_api
<th>run_async
</thead>
<tbody>
<tr>
<td>salesforce_send_twilio_msg
<td>True
<td>True
</tbody>
</table>

Save and move on to the next step.
  
### Service Request

Navigate to the service request table. Create two new rows.
Initally hide the following columns: [call_if, call_for_each]

<table>
<thead>
<tr>
<th>Integration
<th>Sequence
<th>System
<th>Service Name
<th>Formula Variable
<th>skip_execute_if_no_sub_requests
<tbody>
<tr>
<td>salesforce_send_twilio_msg
<td>1
<td>SALESFORCE
<td>N/A
<td>sw_re
<td>False
<tr>
<td>salesforce_send_twilio_msg
<td>2
<td>TWILIO
<td>N/A
<td>tw_re
<td>False
</table>                            |

formula_variable is used for both request and response creation. Access to the variable set here is provided within the integration once the service request process starts.

Save and move on to the next step!

### Field Mapping

Navigate to the Field Mapping Builder.

<table>
<thead>
<tr>
<th>Service Request
<th>Sequence
<th>Field
<th>Value
<th>Value Type
<th>Nullable
</thead>
<tbody>
<tr>
    <td>sw_re
    <td>1
    <td>service_path
    <td>/api/salesforce
    <td>str
    <td>False
<tr>
    <td>sw_re
    <td>1
    <td>method
    <td>"GET"
    <td>str
    <td>
<tr>
    <td>sw_re
    <td>1
    <td>method
    <td>"POST"
    <td>str
    <td>False
<tr>
    <td>tw_re
    <td>1
    <td>body.name
    <td>sw_re.payload.data
    <td>str
    <td>False
<tr>
    <td>tw_re
    <td>1
    <td>body.length
    <td>sw_re.payload.data
    <td>str
    <td>False
<tr>
    <td>tw_re
    <td>1
    <td>service_path
    <td>"api/twilio"
    <td>str
    <td>False
<tr>
<tr>
</tbody>
</table>

The meat of the work is done! Now to call our endpoint let's grab a sample ID from salesforce.
Navigate back to salesforce, click on an account within the new playground... ->>> ADD MORE HERE

### Send Request

Within Glyue, navigate to the SwaggerAPI. This is the easiest way to trigger integrations using Glyue as it will handle all necessary authentication.
Open the newly created endpoint and in the input body for the payload put the in the payload as so.

{
    "account_name": {your_acc_identifier}
}

Press execute. The response from within the swagger page should show a `Integration Completed Successfully`.

Navigate to the Run-History page. Here you can see the specific steps for the integration.

### Alternative: use a REST API client like Insomnia, or Postman

Use basic auth for the authentication. Create a new endpoint.
