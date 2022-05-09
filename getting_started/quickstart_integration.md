
# 20-Minute Example Integration

## Purpose

This is a quick sample to show a walk-through for a basic integration connecting salesforce and twilio to send a notification regarding the status of client.

## Assumptions

- basic knowledge of reading and understanding json
- basic knowledge of python

## Setup

First we will need to setup a salesforce environment for us to use.

Navigate to salesforce ->
----- insert setup steps here for basic trailblazer -----

Using credentials from salesforce,

Next we will need to setup a basic twilio setup
----- insert setup steps here for basic twilio setup -----

Using credentials from twilio, navigate to the Admin page.

Navigate to the validate configs page. Press the validate configs button to check if current configs pass an initial ping with the credentials provided. If your credentials are invalid, go back to the Admin page for your specific adapter and confirm that credentials provided are correct.

### Integration

Navigate to the build page. Add a new row for the integration table. Fill out the `path_name`, and set the `http_api` dropdown to `True`.

<!-- markdownlint-disable no-inline-html -->
<table>
<thead>
<tr>
<td>path name
<td>http_api
<td>run_async
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
