# Glyue SSO: Explanation

[Single Sign-On](https://en.wikipedia.org/wiki/Single\_sign-on) (SSO) is a demanded feature for most contemporary web applications, as it allows for centralized user access control by the business or organization. Users also do not need to worry about forgetting passwords, as they only need their SSO login details to access any of their connected applications.

### SAML vs. OIDC (OpenID) <a href="#glyuesso-explanation-samlvs.oidc-openid" id="glyuesso-explanation-samlvs.oidc-openid"></a>

SSO can be implemented in different ways, the two most common being [SAML](https://en.wikipedia.org/wiki/Security\_Assertion\_Markup\_Language) and [OIDC](https://en.wikipedia.org/wiki/OpenID).

Most internet users will be familiar with a “Login with Google / Twitter / Facebook” option when creating an account or otherwise authenticating with websites such as online stores or social media. Usually, this is OIDC, and is most common for general website users/customers as opposed to employees or members of an organization. For enterprise organizations with a federated identity/access manager, SAML more common.

Glyue uses the SAML 2.0 protocol for its Single Sign On (SSO) and does not support OIDC at this time.

{% hint style="info" %}
For a deeper explanation as to the differences between SAML and OIDC, see [this excellent article](https://jumpcloud.com/blog/saml-vs-openid) from [JumpCloud](https://jumpcloud.com/), a respected cloud-based authentication provider and IT asset management platform.
{% endhint %}

### Brief Overview of SAML and Glyue SSO <a href="#glyuesso-explanation-briefoverviewofsamlandglyuesso" id="glyuesso-explanation-briefoverviewofsamlandglyuesso"></a>

In a SAML SSO configuration, Glyue acts as the **Service Provider (SP)** and a trusted platform (such as JumpCloud, Azure AD, Okta, etc.) acts as the **Identity Provider (IdP)**. Glyue SSO is designed to be IdP-agnostic and work with any provider.

{% hint style="info" %}
While expected to work with any IdP, Glyue SSO is verified to be compatible with JumpCloud, Okta, and Azure AD as of the writing of this article.
{% endhint %}

In general terms, the SP and IdP establish trust by exchanging SAML metadata, an XML document laying out what each provider expects or requires from the other, and which SAML abilities they support (like HTTP POST vs REDIRECT).

From there, the IdP and SP will then communicate securely over HTTP/TLS, with the SP sending sending the user and an authentication request to the IdP, and the IdP responding with a signed SAML assertion (essentially a digital ID card) after the user is authenticated there. The SP verifies the signature of the IdP and then logs the user in. Since all communication is encrypted over the net, and the IdP signature verified on very SAML assertion, the risk for [man-in-the-middle attacks](https://en.wikipedia.org/wiki/Man-in-the-middle\_attack) is significantly reduced.

After configuring Glyue and the IdP to communicate (and with relevant user accounts created), users will be able to log in to Glyue without a username, email address, or password.

If logged in straight to the IdP, the user will most likely see Glyue in their available applications (alongside others like Salesforce, Tableau, Office 365) and can simply click its link to be redirected to Glyue and automatically logged in. This is called IdP-initiated SSO.

Alternatively, on the Glyue login page a button to the IdP should be displayed, allowing the user to authenticate there and be redirected back. This is called SP-initiated SSO.
