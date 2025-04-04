# 2. Vault Setup

{% hint style="warning" %}
To perform the following steps, the user must be a Glyue administrator for the target environment.
{% endhint %}

In this step, we will make use of Glyue's vault feature as a data store for our list of customers. To learn about vault and its full suite of methods, visit [this guide for more information](vault-code-examples-and-explanation.md).

### Create Vault

Log into Glyue and navigate to the **Vault** page.

<figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

Click on the **Create Vault** button, name the vault **data**, and save by clicking on the button again or pressing enter on your keyboar&#x64;**.**&#x20;

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

You should see the newly created vault on the **Vault** page.

<figure><img src="../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

### Create Vault Item

{% hint style="warning" %}
To perform the following steps, the user must be a Glyue administrator for the target environment.
{% endhint %}

We will create a vault item containing a list of customer information. Each customer will have an id, first name, last name, birth date, and a social security number.

To create a vault item, click on the **data** vault to highlight it and click on the **Create Vault Item** button. Name the vault item key **customers** and add a value of `[]` for the vault item key.&#x20;

Save the vault item.&#x20;

<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

The **data** vault should now have a vault item named **customers.**

<figure><img src="../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

### **Add Vault Permissions**

{% hint style="warning" %}
To perform the following steps, the user must be a Glyue administrator for the target environment.
{% endhint %}

Log into Glyue, if necessary and navigate to the **Admin** site.

Scroll to the **Configuration** section, locate **Vault Permissions** and click **Add**.

On the **Add** **Vault Permissions** page, select **data** from the **Vault** dropdown menu, select the integration `get_all_customers` from the Integration dropdown menu, and check the boxes **Read** and **Write**.&#x20;

Click on the **Save** button belo&#x77;**.**

<figure><img src="../../.gitbook/assets/image (9) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Add a vault permission for each integration we had created.

<figure><img src="../../.gitbook/assets/image (32) (1).png" alt=""><figcaption></figcaption></figure>
