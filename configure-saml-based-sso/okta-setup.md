# Okta Setup

Before continuing, this user should be an Okta admin for the organization, and a SAML Config must be created in the Glyue Environment.

### Create the Glyue application in Okta <a href="#oktasso-basicsetuphowto-createtheglyueapplicationinokta" id="oktasso-basicsetuphowto-createtheglyueapplicationinokta"></a>

From the Okta dashboard, find **Applications** on the left-hand panel and select **Applications** under it.



Click the **Create App Integration** button.



Select **SAML 2.0** and click **Next**



Give the app a name. We suggest something like **Glyue DEV**, **Glyue PROD** etc. Click **Next**.



### Provide Glyue’s SAML info to Okta <a href="#oktasso-basicsetuphowto-provideglyuessamlinfotookta" id="oktasso-basicsetuphowto-provideglyuessamlinfotookta"></a>

The Glyue environment SAML metadata will be required for the next step.

Glyue always serves its metadata at `https://` (custom domain) `/sso/saml2/metadata/`. If this user is also a Glyue administrator, the metadata URL will be displayed on the **Admin** site under **SAML Configs**.

#### **Single sign-on URL** <a href="#oktasso-basicsetuphowto-singlesign-onurl" id="oktasso-basicsetuphowto-singlesign-onurl"></a>

In the XML document, locate an element named `AssertionConsumerService` and grab the URL from its `Location` attribute (do not include the `"`).



In most cases this will be `https://` + org domain + `/sso/saml2/acs/`

#### **Audience URI (SP Entity ID)** <a href="#oktasso-basicsetuphowto-audienceuri-spentityid" id="oktasso-basicsetuphowto-audienceuri-spentityid"></a>

In the XML document, locate the first element `EntityDescriptor` and grab the value for its `entityID` attribute. In most cases this will be the same URL of Glyue’s metadata (do not include the `"`).



#### **Attribute Statements** <a href="#oktasso-basicsetuphowto-attributestatements" id="oktasso-basicsetuphowto-attributestatements"></a>

Although the Okta wizard says it is optional, it is actually necessary. Add an attribute called `email`, with `URI Referece` for its **Name format**. Select `user.email` as the **Value**.



Click **Next,** provide feedback to Okta if so inclined, and click **Finish**.

### Get the Okta metadata for Glyue <a href="#oktasso-basicsetuphowto-gettheoktametadataforglyue" id="oktasso-basicsetuphowto-gettheoktametadataforglyue"></a>

From the **Applications** screen, click the newly created application and go to the **Sign On** tab.

Under **Settings** > **Sign on methods** > **SAML 2.0** > **Metadata details**, grab the **Metadata URL**.



This will be needed on the Glyue side, when adding this Okta environment as an IdP. If this user is not a Glyue admin, please provide the URL to a Sandbox Banking employee.

### Lastly… <a href="#oktasso-basicsetuphowto-lastly..." id="oktasso-basicsetuphowto-lastly..."></a>

Don’t forget to assign users or groups to the new Okta application- otherwise they won’t be able to authenticate with Glyue via Okta SSO.
