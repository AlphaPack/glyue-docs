# 2. Calling the External System

**Create the Service Request**

{% hint style="success" %}
A new feature called [**Buildhelper**](buildhelper.md) is now available to help creating new Service Requests for various external Systems / APIs with pre-created fields for various request types.
{% endhint %}

Now that the integration has been created, we can begin to add logic to it. For this tutorial, we will simply call the `randomuser` API and receive its response.&#x20;

Right click on the integration, click _Go To_, then click _Service Request_.&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot 2024-09-03 at 12.02.49 PM.png" alt=""><figcaption><p>Right click > Go To > Service Request</p></figcaption></figure>

You will see an empty table.

On the toolbar along the bottom of the screen, click the plus icon (+) to add a new Service Request. This will create a new row in the table, which will be highlighted in green to indicate it was newly created.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-09-03 at 12.03.01 PM.png" alt=""><figcaption><p>Newly created, empty Service Request</p></figcaption></figure>

We need to fill out three columns on this service request. You may need to scroll your screen to the right to see all of them.&#x20;

| Column           | Value           |
| ---------------- | --------------- |
| System           | `HTTP`          |
| Service Name     | `n/a`           |
| Formula Variable | `request_users` |

Save your changes by clicking the _Save_ icon on the bottom toolbar.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-09-03 at 12.04.34 PM.png" alt=""><figcaption><p>Filled out Service Request</p></figcaption></figure>

Next, we will create the Field Mappings for this Service Request.



**Create the Field Mappings**

Right click along the service request's row, then click _Go To_, then click _Field Mapping_. You will see an empty table.

{% hint style="info" %}
You can verify that you're on the correct page by checking the _Component_ dropdown on the top-left of the page. At this step, it should read "Field Mapping".\
\
![](<../../../.gitbook/assets/Screenshot 2024-09-03 at 12.05.44 PM.png>)
{% endhint %}

Create two new field mappings by clicking the plus icon (+) on the bottom toolbar twice. Fill out the first field mapping by entering the following values in the first row:

| Column     | Value    |
| ---------- | -------- |
| Field      | `method` |
| Value      | `"GET"`  |
| Value Type | `str`    |

Then, fill out the second field mapping with the following values:

| Column     | Value               |
| ---------- | ------------------- |
| Field      | `url_path`          |
| Value      | `"/api/randomuser"` |
| Value Type | `str`               |

<figure><img src="../../../.gitbook/assets/Screenshot 2024-09-03 at 12.07.23 PM.png" alt=""><figcaption><p>Two field mappings, <code>method</code> and <code>url_path</code></p></figcaption></figure>

Save your changes.
