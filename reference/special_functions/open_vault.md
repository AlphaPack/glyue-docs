# open\_vault

`open_vault(vault_name:str) -> Vault`

Opens a vault based on the given name.

{% hint style="info" %}
Read more about the Vault on its main documentation page.
{% endhint %}

**Get data from vault**

```python
with open_vault('data') as vault: 
    # Get data from a vault entry
    customers = vault.get('customers')
```

**Modify data in an existing vault**

```python
new_customer = {"name": "David"}

with open_vault('data') as vault: 
    customers = vault.get('customers')
    customers.append(new_customer)
    vault.update('customers', customers)
```
