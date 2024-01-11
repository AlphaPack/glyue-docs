# Integration Config



### integration

<mark style="color:blue;">`relationship`</mark> - <mark style="color:red;">`required`</mark>

Integration this config is bound to.

### email\_on\_success

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Enable to send emails on successful Integration runs.

### email\_on\_success\_to\_addresses

<mark style="color:yellow;">`string`</mark> - <mark style="color:purple;">`comma separated`</mark>

Valid email addresses that will be sent emails based on successful integration completion.

### email\_on\_failure

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Enable to send emails unsuccessful Integration runs.

### email\_on\_failure\_to\_addresses

<mark style="color:yellow;">`string`</mark> - <mark style="color:purple;">`comma separated`</mark>

Valid email addresses that will be sent emails based on failed integration runs.

### email\_digests

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Enables a more detailed breakdown of the Integration Run for both the [#email\_on\_success](integration-config.md#email\_on\_success "mention") and [#email\_on\_failure](integration-config.md#email\_on\_failure "mention") features.&#x20;

### store\_run\_history

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Enables persistence of run histories for integrations. With this flag disabled the Integration Run History will not track run events.

### store\_run\_history\_for\_x\_days

<mark style="color:yellow;">`integer`</mark>

Number of days to keep Run Histories. After this date the runs are deleted permanently. Defaults to 730 days.

### store\_payload\_in\_run\_history

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Enables persistence of run history payloads for Integration Run Steps. The [#store\_run\_history](integration-config.md#store\_run\_history "mention") must be enabled for this to be enabled.

### store\_payloads\_in\_run\_history\_for\_x\_days

<mark style="color:yellow;">`integer`</mark>

Number of days to persist Integration Run History Items. After this date run history payloads are deleted permanently. Defaults to 14 days.

### engine\_version

Engine version used when running this integration.

```
engine_version = "1.1.0"
```
