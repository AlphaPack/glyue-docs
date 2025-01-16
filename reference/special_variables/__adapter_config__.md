# \_\_adapter\_config\_\_

`__adapter_config__ -> {}`&#x20;

Exposes properties of an adapter config to be overridden using field mappings or in lifecycle hooks.&#x20;

{% hint style="info" %}
Overrides must occur during the `before_prepare_request_hook` or later. See the [full service request hook lifecycle order here](../integration-lifecycle.md#service-request-overview).
{% endhint %}

Values set on the `adapter_config` object will be used for the duration of that service request, in place of the original value set on the adapter config,  for the duration of the Service Request.&#x20;

Subsequent service requests that use the same system/adapter will revert to using the original value set on the adapter config.

{% hint style="warning" %}
Values stored within Field Mappings do not have the same encryption methods as fields set directly on adapter configs. &#x20;

**Do not put sensitive information, including API secrets / passwords, in field mappings or lifecycle hooks.**
{% endhint %}

```
__adapter_config__.username = "temporary_username"

__adapter_config__.host = "other.website.com"
```
