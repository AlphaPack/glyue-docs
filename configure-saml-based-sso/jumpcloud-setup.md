# JumpCloud Setup

Before continuing, this user should be a JumpCloud admin for the organization, and a SAML Config must be created in the Glyue Environment.

### Create the Glyue SSO Application in JumpCloud <a href="#jumpcloudsso-basicsetuphowto-createtheglyuessoapplicationinjumpcloud" id="jumpcloudsso-basicsetuphowto-createtheglyuessoapplicationinjumpcloud"></a>

From the JumpCloud dashboard, select **SSO** from the left-hand navbar and click the **Add New Application** button.



At the bottom of the page, click the **Custom SAML App** button.



Provide a **Display Label**. We recommend something like **Glyue DEV, Glyue PROD**, etc. Provide a **Description** if desired.



### Provide Glyue’s SAML Metadata to JumpCloud <a href="#jumpcloudsso-basicsetuphowto-provideglyuessamlmetadatatojumpcloud" id="jumpcloudsso-basicsetuphowto-provideglyuessamlmetadatatojumpcloud"></a>

Click the **SSO** tab.

The Glyue environment SAML metadata will be required for the next step.

Glyue always serves its metadata at `https://` (custom domain) `/sso/saml2/metadata/`. If this user is also a Glyue administrator, the metadata URL will be displayed on the **Admin** site under **SAML Configs**.

Click the **Upload Metadata** button and upload the metadata provided by Glyue.



Provide a custom **IdP Entity ID**. Any unique value will do.



### Add Users <a href="#jumpcloudsso-basicsetuphowto-addusers" id="jumpcloudsso-basicsetuphowto-addusers"></a>

On the **User Groups** tab users/groups can be assigned to the application. Only assigned users/groups will be able to authenticate with Glyue via JumpCloud.



Add the desired users/groups for the organization. This can also be done later.

### Activate the SSO App <a href="#jumpcloudsso-basicsetuphowto-activatethessoapp" id="jumpcloudsso-basicsetuphowto-activatethessoapp"></a>

Click **Activate** at the bottom of the screen.

Back in **Configured Applications**, select the new SSO App and click **Export Metadata.**



An XML file should be downloaded. This file will be needed on the Glyue side in order to add JumpCloud as an IdP, which is the last step. If not a Glyue admin, please provide this file to a Sandbox Banking employee.
