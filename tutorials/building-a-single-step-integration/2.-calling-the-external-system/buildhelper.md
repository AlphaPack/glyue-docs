# Buildhelper

## Feature Overview <a href="#buildhelper-featureoverview" id="buildhelper-featureoverview"></a>

**Buildhelper** is a tool within Integration Gateway (formerly known as Glyue) that aims to make the process of building new Service Requests without having to start from nothing.

### Import Service Request <a href="#buildhelper-importservicerequest" id="buildhelper-importservicerequest"></a>

The **Import** **Service Request** feature assists the integration developer to create new Service Requests for supported Systems (aka Adapters) with predefined Field Mapping rows. This saves the developer the trouble of referencing API documentation outside Glyue to ascertain the payload structure of the request (i.e. the fields).&#x20;

It functions as a “wizard” where the developer selects the System they are building against, then the applicable Service, then Field Mappings, and then importing options.

A **Service** is simply a grouping of related request types for a given System. Often, this is because the requests perform actions on the same object in the target system, or they all share a similar URL path.&#x20;

{% hint style="info" %}
Imagine a “Persons” service on a ReSTful API that has separate URL paths and/or HTTP methods for creating, editing, getting, and deleting persons. Each of those Service functions would have its own set of Field Mappings.&#x20;

So, for a Service Request to edit an existing Person object in a figurative API:

* The Service Request’s **Service Name** would be `Persons` and,
* The applicable Field Mapping set might be labeled as `Update Person` or something like `PATCH /persons/{personId}` in the Buildhelper interface.
{% endhint %}

{% hint style="warning" %}
Not all Systems have Services and some Services only have one Field Mapping Set.

Not all Systems/Adapters are yet supported, but we are actively working on generating field metadata for commonly used systems, as well as all new systems going forward.
{% endhint %}

