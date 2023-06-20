# JumpCloud Setup

{% hint style="warning" %}
Before continuing, this user should be a JumpCloud admin for the organization, and a SAML Config must be created in the Glyue Environment.
{% endhint %}

### Create the Glyue SSO Application in JumpCloud <a href="#jumpcloudsso-basicsetuphowto-createtheglyuessoapplicationinjumpcloud" id="jumpcloudsso-basicsetuphowto-createtheglyuessoapplicationinjumpcloud"></a>

From the JumpCloud dashboard, select **SSO** from the left-hand navbar and click the **Add New Application** button.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

At the bottom of the page, click the **Custom SAML App** button.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Provide a **Display Label**. We recommend something like **Glyue DEV, Glyue PROD**, etc. Provide a **Description** if desired.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

### Provide Glyue’s SAML Metadata to JumpCloud <a href="#jumpcloudsso-basicsetuphowto-provideglyuessamlmetadatatojumpcloud" id="jumpcloudsso-basicsetuphowto-provideglyuessamlmetadatatojumpcloud"></a>

Click the **SSO** tab.

{% hint style="info" %}
The Glyue environment SAML metadata will be required for the next step.

Glyue always serves its metadata at `https://`\[domain]`/sso/saml2/metadata/`. If this user is also a Glyue administrator, the metadata URL will be displayed on the **Admin** site under **SAML Configs**.
{% endhint %}

Click the **Upload Metadata** button and upload the metadata provided by Glyue.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Provide a custom **IdP Entity ID**. Any unique value will do.

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

### Add Users <a href="#jumpcloudsso-basicsetuphowto-addusers" id="jumpcloudsso-basicsetuphowto-addusers"></a>

On the **User Groups** tab users/groups can be assigned to the application. Only assigned users/groups will be able to authenticate with Glyue via JumpCloud.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Add the desired users/groups for the organization. This can also be done later.

### Activate the SSO App <a href="#jumpcloudsso-basicsetuphowto-activatethessoapp" id="jumpcloudsso-basicsetuphowto-activatethessoapp"></a>

Click **Activate** at the bottom of the screen.

Back in **Configured Applications**, select the new SSO App and click **Export Metadata.**

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

An XML file should be downloaded. This file will be needed on the Glyue side in order to add JumpCloud as an IdP, which is the last step. If not a Glyue admin, please provide this file to a Sandbox Banking employee.

{% hint style="warning" %}
### Lastly… <a href="#azuresso-basicsetuphowto-lastly..." id="azuresso-basicsetuphowto-lastly..."></a>

Don’t forget to assign users or groups to the new application- otherwise they won’t be able to authenticate with Glyue via SSO.
{% endhint %}
