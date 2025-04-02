# 2. Service Request Setup

**Creating the Service Request**\
\
&#xNAN;_&#x46;or reference:_ [_Service Request Documentation_](../../glyue-technical-reference/integration_components/servicerequest.md)\
\
Click on the "View Site" button at the top right of the page to return to the main Glyue UI. From here, you'll need to navigate back to the Build screen.\
\
Right click on the Integration you created and Go To -> Service Requests. Add a new row to this table. \
\
Set the Sequence Number to 1, as this service request should represents the first API call to CodeConnect.\
\
Underneath the System column, enter "CODECONNECT.IBS" to determine which system we are calling out to. (Replace this with "CODECONNECT.HORIZON" or other applicable cores if necessary).

**Configuring the Service Request**\
\
To complete the next steps, you may need to reference the latest CodeConnect documentation that is available on the CodeConnect portal. \
\
For our example in this How-To Guide, we will be using the Get Customer (IBS Customer Information - v2) endpoint to retrieve information about a given customer on the IBS core.\
\
In the Build Page, enter the service name "IBSCI/v2" or whichever IBS service you want to use. This establishes which API group the service request will use within CodeConnect. \
\
Under formula variable, we recommend entering a formula name that corresponds to what the service is doing. In our example case, we use a formula variable of "getCustomer" as it accurately describes what our service is doing. \
\
Click the Save button at the bottom of the screen.

<figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>
