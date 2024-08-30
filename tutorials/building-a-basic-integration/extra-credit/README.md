# 7. Extra credit

### Triggering `hackernews_email_digest` from outside Glyue <a href="#wrappingup-extracredit-triggeringhackernews_email_digestfromoutsideglyue" id="wrappingup-extracredit-triggeringhackernews_email_digestfromoutsideglyue"></a>

{% hint style="info" %}
[Postman](https://www.postman.com/) (an HTTP client for testing APIs) must be installed to proceed.&#x20;
{% endhint %}

1. Download and install Postman if not already done.  Open Postman.
2. Import this collection: [extra\_credit.json.md](extra\_credit.json.md "mention")
3. Go to the collection variables and replace them with the appropriate values.
4. Go to the `hackernews_email_digest` request in the collection and click **Send**.

Integrations aren’t usually triggered by Postman specifically, but it provides us with a way to fine-tune http requests and test APIs. Any external application that wants to trigger a Glyue integration will need the URL as well as the username and password for a Glyue user who has integration execution permissions.  Usually, a "service account" user is created for this purpose.

#### Extra-Extra Credit: <a href="#wrappingup-extra-extracredit" id="wrappingup-extra-extracredit"></a>

If the reader has access to an external system such as Salesforce, or some other CRM, POS, or LOS, why not try setting up that system to communicate with Glyue, using the Postman collection as an example?
