# How to Set Up Single Sign On (SSO)

​[Single Sign-On](https://en.wikipedia.org/wiki/Single_sign-on) (SSO) is a demanded feature for most contemporary web applications, as it allows for centralized user access control by the business or organization. Users also do not need to worry about forgetting passwords, as they only need their SSO login details to access any of their connected applications.

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

## Frequently Asked Questions / FAQ

#### Does Glyue support OIDC (OpenID Connect)?

> No. For a deeper explanation as to the differences between SAML and OIDC, see [this excellent article](https://jumpcloud.com/blog/saml-vs-openid) from [JumpCloud](https://jumpcloud.com/), a respected cloud-based authentication provider and IT asset management platform.

#### Does a user need an account in Glyue before being able to log in via SSO?

> No.  By default users are auto-created if coming from an installed IdP.
>
> This feature can be toggled off if asked.
>
> On the Identity Provider record on the Admin site, it can be set to automatically add users to an organization and/or mark as staff.  If the Default Staff Group or Default Non-Staff Group are set on the Global Config, new users will be added to those groups as appropriate depending on staff status.
>
> This way, user onboarding can be completely automated, so new users are added to your Organization (if using Organizations) as well as added to a Group with permissions to certain integrations.

#### Is it possible for Glyue to create user accounts as needed if they come from a trusted IdP?

> Not at this time, but if you want this feature added to Glyue please let us know!

#### Can I restrict users to logging in with SSO only?

> Yes. New users can be restricted to SSO by unchecking "Allow Password Login" on the invite page. If the user already exists, go to Admin > Accounts, select the account, and uncheck "Allow password auth" and save.

