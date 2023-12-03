# Adapter Configs

### Add Adapter Configs and bind them to the integration <a href="#step3-adapterconfigs-addadapterconfigsandbindthemtotheintegration" id="step3-adapterconfigs-addadapterconfigsandbindthemtotheintegration"></a>

Before we add any **Service Requests** to the integration, we need to add **Adapter Configs** for each system we’re connecting to. In this case the Hacker News API and Gmail SMTP.

{% hint style="info" %}
**Adapters** are modules in Glyue that handle authentication as well as sending and receiving information with external systems. Each of them will need some initial configuration before they can be used.
{% endhint %}

#### Adapter Config setup for Hacker News API <a href="#step3-adapterconfigs-adapterconfigsetupforhackernewsapi" id="step3-adapterconfigs-adapterconfigsetupforhackernewsapi"></a>

There isn’t a specific Glyue adapter for this system. As such, we’re going to use Glyue’s Generic HTTP Adapter which can be used for just about any HTTP API.

{% content-ref url="../../reference/adapters/generic-http-adapter.md" %}
[generic-http-adapter.md](../../reference/adapters/generic-http-adapter.md)
{% endcontent-ref %}

1. Navigate to the Admin site and under **CONFIGURATION**, locate **Adapter Configs: HTTP** (not Email HTTP) and click **➕ Add**.
2. Enter the following values and then save:
   * **Name**: `hackernews`
   * **Active:** ☑️ (checked)
   * **Validation enabled**: ☑️ (checked)
   * **Host:** `hacker-news.firebaseio.com`
   * **Port:** `443`
   * **Basic auth username**: (leave blank)
   * **Basic auth password**: (leave blank)
   * **Server auth cert**: (leave empty)
   * **Client auth cert**: (leave empty)
   * **Timeout seconds**: `60`
3. Now, under **CONFIGURATION**, locate **Adapter Config Bindings** and click **➕ Add**.
   1. Select `hackernews_email_digest` as the **Integration**.
   2. Select `hackernews` as the **Adapterconfig**.
   3. Don’t bother adding an optional user.
   4. Save.

#### Adapter config setup for Gmail SMTP <a href="#step3-adapterconfigs-adapterconfigsetupforgmailsmtp" id="step3-adapterconfigs-adapterconfigsetupforgmailsmtp"></a>

{% hint style="warning" %}
At this point, the reader must have their SMTP credentials ready. [This Google support article](https://support.google.com/accounts/answer/185833?hl=en) provides instructions on how to create App Passwords for external applications to access a user’s Google account.
{% endhint %}

{% content-ref url="../../reference/adapters/email-smtp-adapter.md" %}
[email-smtp-adapter.md](../../reference/adapters/email-smtp-adapter.md)
{% endcontent-ref %}

1. On the Admin site, under **CONFIGURATION**, locate **Adapter Configs: Email SMTP** and click **➕ Add**.
2. Enter these values and save:
   * **Name:** `gmail`
   * **Active:** ☑️ (checked)
   * **Validation enabled:** ☑️ (checked)
   * **Host:** `smtp.gmail.com`
   * **Port:** `587`
   * **Tls encrypt:** ☑️ (checked)
   * **Authenticate:** ☑️ (checked)
   * **Auth username:** (the Google email address)
   * **Auth password:** (the created Google App Password)
3. Now, under **CONFIGURATION**, locate **Adapter Config Bindings** and click **➕ Add**.
   * Select `hackernews_email_digest` as the **Integration**.
   * Select `gmail`as the **Adapterconfig**.
   * Don’t bother adding an optional user.
4. Save.

#### Validate Configs <a href="#step3-adapterconfigs-validateconfigs" id="step3-adapterconfigs-validateconfigs"></a>

1. On the main Glyue site navbar, click **Validate** (the checked-circle symbol).
2.  Click the **\[VALIDATE CONFIGS]** button at the top and wait for results. If successful, the results should look like this:

    ```
    Validation passed for these systems:
        hackernews
        gmail
    ```

    If unsuccessful, there will be more information about what caused the failure, including a Python stack trace.
