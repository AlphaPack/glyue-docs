# Azure Setup

Before continuing, this user should be an Azure AD admin for the organization, and a SAML Config must be created in the Glyue Environment.

### Create the Glyue Enterprise Application <a href="#azuresso-basicsetuphowto-createtheglyueenterpriseapplication" id="azuresso-basicsetuphowto-createtheglyueenterpriseapplication"></a>

From the Azure Active Directory overview page, select **Enterprise applications** from the left-hand panel.

![](../.gitbook/assets/794656786.png)

Click **New Application** at the top.

![](../.gitbook/assets/795213846.png)

Click **Create your own application** at the top.

![](../.gitbook/assets/795312129.png)

Provide a name and select **Integrate any other application you don’t find in the gallery (Non-gallery)**. Click **Create** at the bottom of the page.

![](../.gitbook/assets/795148309.png)

Click **2. Set up single sign on** under **Getting Started**, or select **Single sign-on** from the left-hand panel.

![](../.gitbook/assets/794591255.png)

Select **SAML**.

![](../.gitbook/assets/794722362.png)

### Provide Glyue’s metadata to Azure <a href="#azuresso-basicsetuphowto-provideglyuesmetadatatoazure" id="azuresso-basicsetuphowto-provideglyuesmetadatatoazure"></a>

The Glyue environment SAML metadata will be required for the next step.

Glyue always serves its metadata at `https://` (custom domain) `/sso/saml2/metadata/`. If this user is also a Glyue administrator, the metadata URL will be displayed on the **Admin** site under **SAML Configs**.

At the top, select **Upload metadata file.** Select the appropriate file and upload.

![](../.gitbook/assets/795148332.png)

Click **Save** at the top.

![](../.gitbook/assets/794886183.png)

### Add an email claim <a href="#azuresso-basicsetuphowto-addanemailclaim" id="azuresso-basicsetuphowto-addanemailclaim"></a>

We need to add a claim to the SAML configuration in Azure, so that the user’s email address comes over to Glyue in a field titled “email” instead of something else.

On the application **SAML-based Sign-on** page, in section **2 Attributes & Claims** click **Edit**.

![](../.gitbook/assets/794624036.png)

Click **Add new claim** at the top.

![](../.gitbook/assets/794525715.png)

Enter “email” (without the `"`) in the **Name** field. For **Source Attribute** select “user.mail”. Click **Save** in the top-left.

![](../.gitbook/assets/795148338.png)

Depending on the organization’s Azure configuration, the user email field name may differ.

### Get Azure SAML metadata for Glyue <a href="#azuresso-basicsetuphowto-getazuresamlmetadataforglyue" id="azuresso-basicsetuphowto-getazuresamlmetadataforglyue"></a>

On the application **SAML-based Sign-on** page, in section **3** under **SAML Certificates** download the **Federation Metadata XML**.

![](../.gitbook/assets/794492954.png)

Alternatively, grab the **App Federation Metadata Url** instead of downloading the file.

This will be needed on the Glyue side, to add Azure as an IdP. If this user is not a Glyue admin, please provide the file/URL to a Sandbox Banking employee.

### Lastly… <a href="#azuresso-basicsetuphowto-lastly..." id="azuresso-basicsetuphowto-lastly..."></a>

Don’t forget to assign users or groups to the new application- otherwise they won’t be able to authenticate with Glyue via SSO.
