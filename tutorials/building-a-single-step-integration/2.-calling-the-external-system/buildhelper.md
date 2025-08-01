---
description: >-
  Buildhelper is a tool within Integration Gateway (formerly known as Glyue)
  that aims to provide a basic starting point for Service Requests against an
  external API or System.
---

# Buildhelper

## Importing a Service Request <a href="#buildhelper-importservicerequest" id="buildhelper-importservicerequest"></a>

The **Import** **Service Request** feature assists the integration developer to create new Service Requests for supported Systems (aka Adapters) with predefined Field Mapping rows. This saves the developer the trouble of referencing API documentation outside Glyue to ascertain the payload structure of the request (i.e. the fields).&#x20;

{% hint style="warning" %}
Referencing external API documentation is still recommended.
{% endhint %}

Buildhelper functions as a “wizard” where the developer selects the System they are building against, then the applicable Service, then Field Mappings, and then import options.

{% hint style="info" %}
A **Service** is simply a grouping of related request types for a given System. Often, this is because the various request types will perform different actions on the same object/record in the target system.

#### Example

Imagine a “Customer” service on an arbitrary ReSTful API that has separate URL paths and HTTP methods for creating, editing, getting, and deleting Customer records in the target System.

Let's say we want to edit and existing Customer record.  The Service Request would look something like this:

* The Service Request’s **Service Name** would be `Customer`
* The applicable Field Mapping set might be labeled as `Update Customer` or similar
* The Buildhelper will provide all fields for this type of request
{% endhint %}

{% hint style="warning" %}
Not all Systems have Services and some Services only have one Field Mapping Set.

Not all Systems/Adapters are yet supported, but we are actively working on generating field metadata for commonly used systems, as well as all new systems going forward.
{% endhint %}

### Usage

1.  Open the Buildhelper interface on the Build page by clicking the **Buildhelper** button on the bottom bar. \


    <figure><img src="../../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>
2.  Select the target system.\


    <figure><img src="../../../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>
3.  Select the applicable Service.\


    <figure><img src="../../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>
4.  Select the applicable Field Mapping set.\


    <figure><img src="../../../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>
5.  A preview of the Field Mappings will be displayed. Click the bottom button: **Accept and Proceed to Import Options.**\


    <figure><img src="../../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>
6.  Name your new Service Request (the Formula variable), select an existing Integration to add the Service request to, or create a new Integration with this Service Request. Then click **Add Rows to Table.**\


    <figure><img src="../../../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>
7.  The Build page will automatically navigate to show you the imported data.\


    <figure><img src="../../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../../../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
These changes are merely _staged_ and not yet _saved_.  The user must save changes for the data to persist, just like making any other changes on the Build page.
{% endhint %}
