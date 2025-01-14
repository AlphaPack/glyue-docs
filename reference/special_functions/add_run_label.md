# add\_run\_label

`add_run_label(label:str)`

Adds the provided text label to the integration's run history instance. Accepts free-form strings.&#x20;

Run labels are visible in an integration's details within the Run History page.&#x20;

{% hint style="info" %}
The recommended format for searchability is colon-separated pair, e.g. `label:value`
{% endhint %}

```python
# Saving the ID of a loan
add_run_label(f"loan_id:{payload.loan.identifier}")

# Noting a property of the integration with a static label 
add_run_label("type:mortgage")
```
