# 3. Create Web Service Endpoints

We will create a custom web service endpoint for each integration that was setup in the previous step.

{% hint style="info" %}
All integrations can be exposed via the standard `integrations/execute/..` HTTP endpoint. However, a custom web service endpoint will allow you to choose a specific RESTful method (e.g. GET, POST, PUT, PATCH, and DELETE) so that the method reflects the type of web service being called.&#x20;
{% endhint %}

### Add Web Service Endpoints

To create a web service endpoint to retrieve all customers from the **data** vault, log into Glyue, if necessary and navigate to the **Admin** site.

Scroll to the **Configuration** section, locate **Web service endpoints** and click **Add**.

On the **Add Web service endpoint** page, fill in the fields with the following information&#x20;

* **Path** - get\_all\_customers
* **Method** - Get
* **Prefix** - api
* **Integration** - get\_all\_customers
* **Description** - This endpoint will retrieve all customers from the data vault.
* **Response content type** - application/json

<figure><img src="../../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

Click on the **Save** button below.

You should now see the web service endpoint on the **Swagger** page.

<figure><img src="../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

The web service endpoint to retrieve a specific customer requires a path parameter for the Id number. In the path field of a web service endpoint, parameters are enclosed with curly braces (e.g. `path/{parameter}`).&#x20;

To create the web service endpoint to retrieve a specific customer by Id, add another integration config and fill in the fields with the following information&#x20;

* **Path** - get\_customer
* **Method** - Get
* **Prefix** - api
* **Integration** - get\_customer
* **Description** - This endpoint will retrieve a specific customer from the data vault using their Id.
* **Response content type** - application/json

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

Follow the same steps above and view the image below to create the remaining web service endpoints.&#x20;

{% hint style="info" %}
The path name for the update customer and delete customer web service endpoints also have an Id parameter.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>
