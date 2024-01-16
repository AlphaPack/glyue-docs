# Create and configure the integration

1. Log into Glyue and navigate to the **Build** page (click the 🔧 \[wrench] icon on the left-hand navbar).
   1. Make sure that **Integration** is selected under **Component** in the top-left corner.
   2. Click the **\[➕ADD ROW]** button on the bottom.
   3. Double click the new row’s **Path Name** cell and enter `hackernews_email_digest`.
   4.  Under **Description**, click the pop-out symbol (`↗️`) and the editor drawer should open from the bottom, providing more room for writing. Paste this short description of what this integration will do:

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
   5. Click the **\[**💾 **Save]** button on the bottom (or use keyboard shortcut: `CTRL + S`).
2. Navigate to the Admin site by clicking the human silhouette icon (`👤`) in the top-right corner, then selecting "Admin" from the dropdown.
   1. Scroll to the bottom and on the **Integration Config** row, click **\[➕ADD]**.
   2. Select `hackernews_email_digest` from the **Integration** picklist.
   3. Uncheck **Email digests**.
   4. Check the boxes at the bottom for **Store run history** and **Store payloads in run history**. Leave all other options as-is.
   5. Click **SAVE** at the bottom.
   6. At the top, click **VIEW SITE** to leave the admin site and return to the main Glyue interface.
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
Congratulations reader, the integration works!

It doesn’t do much yet though, so let’s continue building.
{% endhint %}
