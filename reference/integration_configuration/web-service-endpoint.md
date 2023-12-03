---
description: >-
  Configuration reference for non-default HTTP(S) integration API paths and
  verbs
---

# Web Service Endpoint

Glyue supports building web services that execute integrations via user-defined URL paths and methods.  Among other use cases, these admin components allow for the construction of traditional RESTful web services as explained in [build-a-restful-crud-web-service](../../how-to-guides/build-a-restful-crud-web-service/ "mention").

{% hint style="warning" %}
**IMPORTANT CAVEAT:**  Only URL paths starting with `/api/` or `/rest/` are currently supported
{% endhint %}

## Fields

<table><thead><tr><th width="179">Name</th><th width="323">Example Value (s)</th><th>Description</th></tr></thead><tbody><tr><td>Path</td><td><code>q2/apps</code>, <code>fiserv-dna</code></td><td>Specifies the endpoint's URL path following the initial <code>/api/</code> or <code>/rest/</code> root fragment. </td></tr><tr><td>Method</td><td><code>Get</code>, <code>Post</code>, <code>Put</code>, <code>Patch</code>, <code>Delete</code></td><td>Specifies the HTTP method (sometimes called a "verb") used for calling the API.  Limited to the example values shown here.</td></tr><tr><td>Prefix</td><td><code>api</code>, <code>rest</code></td><td>Specifies the endpoint URL's root path fragment.  As stated above, all configured web service endpoints must currently be hosted at a URL path starting with either <code>/api/</code> or <code>/rest/</code>.</td></tr><tr><td>Integration</td><td><code>retrieve_q2_applications</code>, <code>create_fiserv_dna_customer</code></td><td>Integration to be executed.  Value is selected from the list of integrations currently existing in the Glyue environment.</td></tr><tr><td>Description</td><td>Retrieves applications from Q2</td><td>Description of the web service endpoint.</td></tr><tr><td>Response content type</td><td><code>application/json</code>, <code>application/html</code>, <code>text/xml</code>, <code>text/html</code>, <code>application/soap+xml</code></td><td>Specifies the integration response type. </td></tr></tbody></table>
