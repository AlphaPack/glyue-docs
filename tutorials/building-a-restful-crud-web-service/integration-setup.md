# 1. Integration Setup

### Add Integration

We will setup an integration for each of the services listed below to read and/or write from/to vault. We will set up and name our vault **data** in the next guide.

* Get all customers
* Get a specific customer by Id
* Create a customer
* Update a customer
* Delete a customer

To create an integration, log into Glyue, if necessary and navigate to the **Build** page. The default component for the **Build** page is the **Integration** table, therefore, click on the **Add Row** button.&#x20;

This integration will retrieve all customers from the **data** vault. Fill in the path name and the description field with the following information.

* **Path Name** - get\_all\_customers
* **Description** - This integration will retrieve all customers from the data vault.

Click on the **Save** button below.&#x20;

<figure><img src="../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

Create an integration for the remaining services as shown in the image below.&#x20;

<figure><img src="../../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

### Add Integration Config

{% hint style="warning" %}
To perform the following steps, the user must be a Glyue administrator for the target environment.
{% endhint %}

Log into Glyue, if necessary and navigate to the **Admin** site.

Scroll to the **Configuration** section, locate **Integration Config** and click **Add**.

On the **Add** **Integration Config** page, select the integration `get_all_customers` from the Integration dropdown menu and check the box **Store payloads in run history for x days**.

Click on the **Save** button belo&#x77;**.**

<figure><img src="../../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

Add an integration config for each integration we had created.
