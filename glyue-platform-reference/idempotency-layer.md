# Idempotency Layer

Glyue features a built-in [idempotency](https://en.wikipedia.org/wiki/Idempotence) layer for all integrations that enables callers of integrations to retry requests without concern of unintentionally duplicating the operation.

When the `Idempotency-Key` header is present, any subsequent calls from the same account with the same `Idempotency-Key` value will be treated as a duplicate request and will be returned the same response (status code + response object) as the initial request **without re-running the integration**_._&#x20;

Resending a request with an already-used `Idempotency-Key` is most appropriate when the client does not receive a response from Glyue, e.g. due to a network connectivity drop. In such situations, retrying a request with the same `Idempotency-Key` will allow the client to safely determine whether the operation actually succeeded, or if it should try again with a new `Idempotency-Key`**.**



### **Activating the Idempotency Layer**

To activate the idempotency layer, add the `Idempotency-Key` header to the request, along with the unique ID.&#x20;

Glyue guarantees that integrations will not be re-run if they are called with the same idempotency id within a 24 hour period, and instead the status and response of the first run will be returned.

IDs may be up to 64 characters long.

{% hint style="info" %}
It is strongly recommended that a UUID generator is used to create the idempotency ID.
{% endhint %}



### Sample Client Code
