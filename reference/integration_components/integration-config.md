# Integration Config

### integration

<mark style="color:blue;">`relationship`</mark> - <mark style="color:red;">`required`</mark>

Integration the config is bound to.

### email\_on\_success

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Determine wheter to send an email summary upon a successful integration run.

### email\_on\_success\_to\_addresses

<mark style="color:yellow;">`string`</mark> - <mark style="color:purple;">`comma separated`</mark>

Email addresses to receive summaries on successful integration completion.

### email\_on\_failure

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Determine wheter to send an email summary upon an integration failure.

### email\_on\_failure\_to\_addresses

<mark style="color:yellow;">`string`</mark> - <mark style="color:purple;">`comma separated`</mark>

Email addresses to receive summaries on integration failures.

### email\_digests

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Enables a more detailed breakdown of the Integration Run for both the [#email\_on\_success](integration-config.md#email_on_success "mention") and [#email\_on\_failure](integration-config.md#email_on_failure "mention") features.&#x20;

### store\_run\_history

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Enables persistence of run histories for integrations. With this flag disabled the Integration Run History will not track run events.

### store\_run\_history\_for\_x\_days

<mark style="color:yellow;">`integer`</mark>

Number of days to keep Run Histories. After this date the runs are deleted permanently. Defaults to 730 days.

### store\_payload\_in\_run\_history

<mark style="color:yellow;">`boolean`</mark> - <mark style="color:red;">`required`</mark>

Enables persistence of run history payloads for Integration Run Steps. The [#store\_run\_history](integration-config.md#store_run_history "mention") must be enabled for this to be enabled.

### store\_payloads\_in\_run\_history\_for\_x\_days

<mark style="color:yellow;">`integer`</mark>

Number of days to persist Integration Run History Items. After this date run history payloads are deleted permanently. Defaults to 14 days.

### engine\_version

Engine version used when running this integration.

```
engine_version = "1.1.0"
```
