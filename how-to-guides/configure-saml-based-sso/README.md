# Single Sign On (SSO)

​[Single Sign-On](https://en.wikipedia.org/wiki/Single\_sign-on) (SSO) is a demanded feature for most contemporary web applications, as it allows for centralized user access control by the business or organization. Users also do not need to worry about forgetting passwords, as they only need their SSO login details to access any of their connected applications.

#### SAML vs. OIDC (OpenID) <a href="#glyuesso-explanation-samlvs.oidc-openid" id="glyuesso-explanation-samlvs.oidc-openid"></a>

SSO can be implemented in different ways, the two most common being [SAML](https://en.wikipedia.org/wiki/Security\_Assertion\_Markup\_Language) and [OIDC](https://en.wikipedia.org/wiki/OpenID).

Glyue uses the SAML 2.0 protocol for its Single Sign On (SSO) and does not support OIDC at this time. For a deeper explanation as to the differences between SAML and OIDC, see [this excellent article](https://jumpcloud.com/blog/saml-vs-openid) from [JumpCloud](https://jumpcloud.com/), a respected cloud-based authentication provider and IT asset management platform.

#### Brief Overview of SAML and Glyue SSO <a href="#glyuesso-explanation-briefoverviewofsamlandglyuesso" id="glyuesso-explanation-briefoverviewofsamlandglyuesso"></a>

In a SAML SSO configuration, Glyue acts as the **Service Provider (SP)** and a trusted identity/access platform (such as JumpCloud, Azure AD, Okta, etc.) acts as the **Identity Provider (IdP)**. Glyue SSO is designed to be IdP-agnostic and work with any provider.

{% hint style="info" %}
While expected to work with any IdP, as of the writing of this article, Glyue SSO is verified to be compatible with:

* JumpCloud
* Okta
* Azure AD

More providers will be added as their compatibility is verified.
{% endhint %}

The usual user authentication flow goes like this:

1. User clicks SSO option on the SP login screen. SP redirects the user to the IdP along with a SAML request.
2. User authenticates at the IdP.  IdP redirects user back to the SP along with a signed SAML response, which contains information on the user it just authenticated.
3. SP verifies the signature, reads the response, identifies the correct user in its system, and logs them in.

Before any of that could happen, though, the service and ID providers had to establish a trusted relationship.  The usual flow for that goes like this:

1. A Glyue administrator configures and activates SAML SSO and then provides a metadata file to the other organization.
2. An IdP administrator at the organization adds Glyue as an SP, uploads the metadata, and configures as necessary. They provide another metadata file back to the Glyue admin.
3. The Glyue admin adds the IdP and uploads its metadata.

Once done, the IdP should appear on the Glyue login screen as an option for users.
