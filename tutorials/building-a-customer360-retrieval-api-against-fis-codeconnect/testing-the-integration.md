# 5. Testing the Integration

Now that all of the setup is complete, you can now test the integration. During this phase, you may run into certain connection or configuration errors; if these do show up, you will need to troubleshoot the issues as necessary.



Navigate to the Swagger API page on the left. Here, you should see a list of **Integration Execution Endpoints**, one of which being the Integration you just created.



Click on the integration and to open the dropdown menu:

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

From here, click on the "Try it out" button in the top left of the menu. This allows us to change the **Input Payload** that we send through the integration. During the [Integration and Service Request Hook Setup](integration-and-service-request-hook-setup.md), if you chose to set the `customerNumber` variable to something within the input payload like this:

```
customerNumber = input.payload.testNumber
keep(customerNumber = customerNumber)
```

Then copy and paste this JSON payload into the Swagger Page:

```json
{
    "testNumber": "00000000001"
}
```

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Click on the "Execute" button to run the integration. After executing, navigate to the Run History Page to see the results of your test. If successful, the output record in run history should look something like this:

<figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>
