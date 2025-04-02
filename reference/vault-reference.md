# Vault Reference

All vault functions must be used with an "opened" vault.

```
with open_vault('applications') as vault:
    # Get, insert, update, upsert, or delete vault data
```

Vault Items can be viewed in the UI and are stored unencrypted. They are useful for integration configuration, but should not be used for storing secrets or PII

* `vault.get(key)`
* `vault.insert(key, value, **kwargs)`
* `vault.update(key, value)`
* `vault.upsert(key, value)`
* `vault.delete(key)`

&#x20;Vault Secrets cannot be read in the UI and are stored encrypted. They are suitable for storing secrets, and may be suitable for storing small amounts of information, such as account numbers, on a temporary basis if needed by the integration.

* `vault.get_secret(key)`
* `vault.insert_secret(key, value)`
* `vault.update_secret(key, value)`
* `vault.upsert_secret(key, value)`
* `vault.delete_secret(key)`
