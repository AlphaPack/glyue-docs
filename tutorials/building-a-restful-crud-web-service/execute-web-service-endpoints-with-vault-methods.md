# 4. Execute Web Service Endpoints with Vault Methods

To execute any of the web service endpoints setup in the previous step (e.g. get all customers, get customer by Id, update customer, and delete customer), we must first write code in each of the connected integrations to open, read, and/or write to the **data** vault.

### Get All Customers

Log into Glyue, if necessary and navigate to the **Build** page. Select the `get_all_customers` integration and add the following [code](https://app.gitbook.com/o/hMR7ZmLUVPDLpu0EFvkY/s/1flQ2To8tQpCQWl2Ty9U/~/changes/84/build-a-restful-crud-web-service-using-vault/code-examples-and-explanation#get-all-customers) in the **Before Hook**.

<figure><img src="../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Assigning a value to `output.payload` allows you to provide the desired content for the response body.
{% endhint %}

Navigate back to the **Swagger** page. Select the web service endpoint `/rest/get_all_customers`_._ Click on the **Try it out** button and the **Execute** button.

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

You should receive text in the response body confirming that there are no customers in the **data** vault.

<figure><img src="../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

On the **Run History** page, you would noticed the integration `get_all_customers` was executed because it is the integration connected to the endpoint `/rest/get_all_customers`. Also, the `input` displays the HTTP method and the full path or web service endpoint that was used to call this integration.&#x20;

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

In the next step, we will execute this web service endpoint again after we add a new customer in the **data** vault.&#x20;

### Add a Customer

In the `add_customer` integration, we will create a service request and several field mappings to insert a customer in the **data** vault. The customer information will come from the body of a request and will contain the customer's first name, last name, birth date, and social security number.

Select the `add_customer` integration to highlight it and right click it to display a context menu.&#x20;

On the context menu, hover over **Go To** or **Go to (New Tab)** and select **Service Request.**&#x20;

<figure><img src="../../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

You will be redirected to the **Service Request** component on the **Build** page. On this page, click on the **Add Row** button at the bottom of the screen and fill in the fields with the following information for this service request.&#x20;

* **Sequence** - 1
* **System** - ECHO
* **Service Name** - N/A
* **Formula Variable** - insert\_customer

Click on the **Save** button below.&#x20;

<figure><img src="../../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

Click on the service request to highlight it and right click it to display a context menu again. On the context menu, hover over **Go To** or **Go to (New Tab)** and select **Field Mapping**.

You will be redirected to the **Field Mapping** component on the **Build** page. On this page, click on the **Add Row** button at the bottom of the screen and fill in the fields with the following information.

* **Sequence** - 1
* **Field** - id
* **Value** - import uuid; retvalue = uuid.uuid4()
* **Value Type** - str

Click on the **Save** button below.&#x20;

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The value of the id field contains code that generates a random UUID number.
{% endhint %}

Add the remaining field mapping rows for the first name, last name, birth date and social security as shown in the image below.&#x20;

<figure><img src="../../.gitbook/assets/image (26) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
We are mapping the first name, last name, birth date, and social security number from `input.payload`. The `input.payload` contains information submitted in the body of a request.
{% endhint %}

Navigate back to the **Swagger** page and select the web service endpoint `/rest/add_customer`_._ Click on the **Try it out** button and add a JSON object of customer information as shown in the image below. Click on the **Execute** button.

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

On the **Run History** page, you would see the integration `add_customer` have the customer information that we submitted in the body of the request within `input.payload`.

<figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

On the **Run History Item**, click on the `insert_customer` request and you would see in the response the field mappings we added in the previous step. We will use `response.payload` of the service request `insert_customer` to add a customer in the **data** vault.

<figure><img src="../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

To add a customer in the **data** vault, navigate to the service request `insert_customer` and add the following [code](https://app.gitbook.com/o/hMR7ZmLUVPDLpu0EFvkY/s/1flQ2To8tQpCQWl2Ty9U/~/changes/84/build-a-restful-crud-web-service-using-vault/code-examples-and-explanation#add-a-customer) in the **After Execute Request Success Hook**.&#x20;

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

Navigate back to the **Swagger** page and execute the web service endpoint `/rest/add_customer` again. _&#x59;_&#x6F;u should receive the id of the customer in the response body.

<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

Insert another customer as shown in the image below and execute the web service endpoint `/rest/add_customer`.

<figure><img src="../../.gitbook/assets/image (12) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Afterwards, execute the web service endpoint `/rest/get_all_customers`. You should see both customers in the body of the response.

<div align="center"><figure><img src="../../.gitbook/assets/image (11) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure></div>

### Get Customer By Id

Navigate back to the **Integration** table on the **Build** page in Glyue and select the integration `get_customer`. Add the following [code](https://app.gitbook.com/o/hMR7ZmLUVPDLpu0EFvkY/s/1flQ2To8tQpCQWl2Ty9U/~/changes/84/build-a-restful-crud-web-service-using-vault/code-examples-and-explanation#get-customer-by-id) in the **Before Hook**.&#x20;

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
`input.path` is the location where path parameter values can be accessed.
{% endhint %}

Navigate back to the **Swagger** page and select the web service endpoint `/rest/get_customer`. Click on the **Try it out** button and add a valid id path parameter as shown in the image below.

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

Click on the **Execute** button. _&#x59;_&#x6F;u should receive the customer's information in the form of a JSON object in the response body.

<figure><img src="../../.gitbook/assets/image (17) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Update Customer

The following steps are similar to what we did to add a customer in the **data** vault. The major difference is we omit the id field because the customer Id should never change.

Create the following service request for the `update_customer` integration.

* **Sequence** - 1
* **System** - ECHO
* **Service Name** - N/A
* **Formula Variable** - modify\_customer

Click on the **Save** button below.&#x20;

<figure><img src="../../.gitbook/assets/image (24) (1).png" alt=""><figcaption></figcaption></figure>

Next, create the following field mapping rows for the service request `modify_customer`.&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

In the field mapping table, we are using the **Call If** column to omit or include a field and value in `response.payload` based on the existence of the field in `input.payload`.&#x20;

Navigate back to the `modify_customer` service request and add the following [code](https://app.gitbook.com/o/hMR7ZmLUVPDLpu0EFvkY/s/1flQ2To8tQpCQWl2Ty9U/~/changes/84/build-a-restful-crud-web-service-using-vault/code-examples-and-explanation#update-customer) in the **After Execute Request Success Hook**.&#x20;

<figure><img src="../../.gitbook/assets/image (17) (1).png" alt=""><figcaption></figcaption></figure>

Navigate back to the **Swagger** page. Select the web service endpoint `/rest/update_customer` and click on the **Try it out** button. Add a valid id path parameter and a new first name and last name in the body of the request as shown in the image below.&#x20;

<figure><img src="../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

Click on the **Execute** button. You should receive the customer's information in the form of a JSON object with the first name and last name updated.&#x20;

<figure><img src="../../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

### Delete Customer

Navigate back to **Integration** table on the **Build** page in Glyue and select the integration `delete_customer`. Add the following [code](https://app.gitbook.com/o/hMR7ZmLUVPDLpu0EFvkY/s/1flQ2To8tQpCQWl2Ty9U/~/changes/84/build-a-restful-crud-web-service-using-vault/code-examples-and-explanation#delete-customer) in the **Before Hook**. &#x20;

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

Navigate back to the **Swagger** page and select the web service endpoint `/rest/update_customers`. Click on the **Try it out** button and provide a valid id path parameter as shown in the image below.

<figure><img src="../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

You should receive a confirmation message that the customer was deleted.

<figure><img src="../../.gitbook/assets/image (18) (1).png" alt=""><figcaption></figcaption></figure>
