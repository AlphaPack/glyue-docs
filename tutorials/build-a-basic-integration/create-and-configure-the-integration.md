# Create and configure the integration

To start, we will create the scaffolding for the integration by setting up its metadata (name, description, and settings) and its **Adapter Configs.** We'll finish this step by validating that the adapters we created can successfully contact the systems we connected them to.

{% hint style="info" %}
**Adapters** are modules in Glyue that handle authentication, sending, and receiving of information with external systems. Each adapter needs some initial configuration before it can be used, which is stored in an **Adapter Config.**
{% endhint %}



**Create the Integration and Adapter Configs**

1. Log into Glyue and navigate to the **Build** page (click the 🔧 \[wrench] icon on the left-hand navbar).
   1. Make sure that **Integration** is selected under **Component** in the top-left corner.
   2. Click the **\[➕ADD ROW]** button on the bottom.
   3. In the wizard that appears, enter the following:
      1. **Path Name:** `hackernews_email_digest`.
      2.  **Description:**&#x20;

          ```
          Queries the Hacker News API and sends an email with links to the latest top posts.
          Input:
          {
            "email": "email_address@domain.tld",
            "limitQuery": 100,
            "limitEmail": 10
          }
          email:      REQUIRED | str | the email address to send the digest to
          limitQuery: OPTIONAL | int | limit to the number of articles to query
          limitEmail: OPTIONAL | int | max number of articles to send in the email
          ```
      3. Expand the **Email Settings** section and uncheck **Email Digests**
      4. Expand the **Run Settings** section and ensure **Store Run History** and **Store Run History Payloads** are enabled
   4. Click the **Save** button to move to the next page of the wizard.
2. On the **Systems step** of the wizard, we will create two **Adapter Configs,** one for accessing the Hacker News API and another for Gmail SMTP
   1. Click on **Add System** to create the Hacker News API adapter
   2. In the **Available Adapters** dropdown, select **HTTP**
   3. In the **Select Adapter Config** dropdown, select **Add New Adapter** and fill out the following information, then click **Save**:
      1. **Name**: `hackernews`
      2. **Active:** ☑️ (checked)
      3. **Validation enabled**: ☑️ (checked)
      4. **Host:** `hacker-news.firebaseio.com`
      5. **Port:** `443`
      6. **Basic auth username**: (leave blank)
      7. **Basic auth password**: (leave blank)
      8. **Server auth cert**: (leave empty)
      9. **Client auth cert**: (leave empty)
      10. **Timeout seconds**: `60`
   4. Click on **Add System** again, this time to create the Gmail SMTP adapter
   5. In the **Available Adapters** dropdown, select **Email SMTP**
   6. In the **Select Adapter Config** dropdown, select **Add New Adapter** and fill out the following information, then click **Save**:
      1. **Name:** `gmail`
      2. **Active:** ☑️ (checked)
      3. **Validation enabled:** ☑️ (checked)
      4. **Host:** `smtp.gmail.com`
      5. **Port:** `587`
      6. **Tls encrypt:** ☑️ (checked)
      7. **Authenticate:** ☑️ (checked)
      8. **Auth username:** (the Google email address)
      9. **Auth password:** (the created Google App Password)
   7. Click **Save Adapter Bindings** on the top right to save the adapters we created, then click **Continue**
   8. On the final page of the wizard, give your user all permissions (Read, Write, Execute, and Debug) for the integration you just created. Click **Save Permissions**, then close the wizard by clicking **Go to build.**



**Verify the Adapter Configs**

1. Return to the Dashboard on the on main Glyue interface.
2.  Click the **\[VALIDATE]** button in the **Adapter Config Validation Results** section and wait for results. If successful, the results should look like this:

    ```
    Validation passed for these systems:
        hackernews
        gmail
    ```

    If unsuccessful, there will be more information about what caused the failure, including a Python stack trace.
3. Navigate to the **Swagger API** page by selecting **API** from the left-hand navbar.
   1. Select `/hackernews_email_digest` and click **Try it out** to expand the Swagger console for this endpoint.
   2. Delete the request body and input: `{}` (an empty JSON object)
   3. Scroll to the bottom and click **Execute**.
   4. Navigate to **Run History** by clicking the circular-arrow-clock icon from the left-hand navbar.
   5. Under the **RUNS** column (the left-most column) there should be a `hackernews_email_digest` record, along with a timestamp, username, and id. Click it.
   6.  Under the next column, **RUNS**, an `INPUT` and `OUTPUT` should appear. Clicking them should display the http request (input) that triggered the integration, as well as its output respectively:

       ```
       {
         "payload": "Integration hackernews_email_digest completed successfully!",
         "headers": {},
         "status": 200
       }
       ```

{% hint style="success" %}
Congratulations, the integration works!

It doesn’t do much yet though, so let’s continue building.
{% endhint %}
