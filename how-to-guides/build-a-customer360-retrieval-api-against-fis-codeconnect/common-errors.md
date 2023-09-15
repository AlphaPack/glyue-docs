---
description: >-
  Here are some common errors and resolutions you may run into when testing the
  CodeConnect integration.
---

# Common Errors

### IntegrationConfig matching query does not exist:

{% code fullWidth="true" %}
```
Traceback (most recent call last):
  File "/glyue/django_glyue_app/integration_engine.py", line 403, in _validate_integration
    models.IntegrationConfig.objects.get(integration=integration)
  File "/usr/local/lib/python3.8/dist-packages/django/db/models/manager.py", line 85, in manager_method
    return getattr(self.get_queryset(), name)(*args, **kwargs)
  File "/usr/local/lib/python3.8/dist-packages/django/db/models/query.py", line 435, in get
    raise self.model.DoesNotExist(
django_glyue_app.models.IntegrationConfig.DoesNotExist: IntegrationConfig matching query does not exist.

```
{% endcode %}

To solve this error, please create an IntegrationConfig record as explained in [Integration Setup.](integration-setup.md)

***

### customerNumber is not defined:

{% code fullWidth="true" %}
```
Traceback (most recent call last):
  File "/glyue/django_glyue_app/integration_engine.py", line 1287, in _apply_fieldmapping
    value = self.eval_formula(value)
  File "/glyue/django_glyue_app/integration_engine.py", line 1651, in eval_formula
    return eval(formula, namespace)
  File "<string>", line 1, in <module>
NameError: name 'customerNumber' is not defined
```
{% endcode %}

To solve this error, ensure that you've followed the steps in [Integration and Service Request Hook Setup](integration-and-service-request-hook-setup.md); specifically, ensure that you are setting the variable `customerNumber` to a defined value and using `keep()` to make it useable within the Field Mapping Table.

***

### Failed to load adapter configuration for CODECONNECT.IBS:

{% code fullWidth="true" %}
```
Traceback (most recent call last):
  File "/glyue/django_glyue_app/integration_engine.py", line 1396, in _execute_request
    adapter.load_adapter_config()
  File "/glyue/django_glyue_app/adapters/__init__.py", line 93, in load_adapter_config
    raise ObjectDoesNotExist(f"No active adapter config bound to integration")
django.core.exceptions.ObjectDoesNotExist: No active adapter config bound to integration

```
{% endcode %}

To solve this error, ensure that you've created an Adapter Config Binding between the integration you are testing and the CodeConnect Adapter Config as explained in [Integration Setup](integration-setup.md).

***

###
