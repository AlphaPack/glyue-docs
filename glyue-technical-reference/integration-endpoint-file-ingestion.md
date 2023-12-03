---
description: >-
  Glyue supports building and running integration web service APIs that receive
  any arbitrary binary content (e.g. documents, audio/video streams, archives)
---

# Integration Endpoint File Ingestion

Integration execution endpoint request bodies that aren't single JSON or XML documents are converted into one or multiple `GlyueFileHandle` objects and then passed into Glyue's integration engine for processing. &#x20;

These "file ingestion" requests are subject to the following API restrictions:

<table><thead><tr><th width="157">HTTP Method</th><th width="258">HTTP Request with Single File</th><th>HTTP Request with Multiple Files</th></tr></thead><tbody><tr><td>POST</td><td><mark style="color:green;">supported</mark></td><td><mark style="color:green;">supported</mark></td></tr><tr><td>PUT</td><td><mark style="color:green;">supported</mark></td><td><mark style="color:red;">rejected (415 unsupported media type)</mark></td></tr><tr><td>PATCH</td><td><mark style="color:green;">supported</mark></td><td><mark style="color:red;">rejected (415 unsupported media type)</mark></td></tr><tr><td>GET</td><td><mark style="color:yellow;">accepted but body is ignored</mark></td><td><mark style="color:yellow;">accepted but body is ignored</mark></td></tr><tr><td>DELETE</td><td><mark style="color:yellow;">accepted but body is ignored</mark></td><td><mark style="color:yellow;">accepted but body is ignored</mark></td></tr></tbody></table>

{% hint style="warning" %}
By default, integration endpoints only accept POST requests.

To allow an integration to accept requests of other methods, a Web Service Endpoint must be created.  The new Web Service Endpoint URI will differ from the default POST URI for the integration.
{% endhint %}

### Content-Type Handling

Glyue parses integration web service HTTP(S) bodies in accordance with  the request's `Content-Type` header value as follows:

<table><thead><tr><th width="294">HTTP Request Content-Type(s)</th><th>Body Parsing Behavior</th></tr></thead><tbody><tr><td><code>application/json</code></td><td>Parsed as JSON into Pythonic data structure</td></tr><tr><td><code>application/xml</code> or <code>text/xml</code></td><td>Parsed as XML into Pythonic data structure</td></tr><tr><td><code>multipart/form-data</code></td><td>Parsed into one or more <code>GlyueFileHandle</code> objects in accordance to usual <code>multipart/form-data</code> standards</td></tr><tr><td><code>*/*</code> or any other value</td><td>Parsed into one <code>GlyueFileHandle</code> object</td></tr></tbody></table>



{% hint style="info" %}
It is possible to submit a single file in a `multipart/form-data` request.
{% endhint %}

### Multipart / Form-Data Content Requirements

Glyue assumes that the name of the field in the form data is the name of the file in that field.

Non-file form data will appear in `input.payload` while the files will appear in `input.files`.

<table><thead><tr><th width="259"></th><th></th></tr></thead><tbody><tr><td><code>loan</code></td><td><code>FISCHER-20230531</code></td></tr><tr><td><code>note</code></td><td><code>Documents received from applicant today</code></td></tr><tr><td><code>driver_license.tiff</code></td><td>(file data)</td></tr><tr><td><code>bank_statement_01.pdf</code></td><td>(file data)</td></tr></tbody></table>

```
{
    ...
    "headers": {...},
    "payload": {
        "loan": "FISCHER-20230531",
        "note": "Documents received from applicant today"
    },
    "files": {
        "driver_license.tiff": <GlyueFileHandle ... >,
        "bank_statement_01.pdf": <GlyueFileHandle ... >,
    },
    ...
}
```

### Single Binary / File Upload Requirements

Content type for these requests will vary depending on the type of file being sent.  Some common content types that apply are `application/zip`, `application/pdf`, `image/png`, `audio/mpeg`, `video/mp4`, `application/octet-stream`.

#### Content-Disposition Header

In order for Glyue to be aware of the file's name, the request must include it within the `Content-Disposition` in a standards-compliant manner like the following:

<table data-header-hidden><thead><tr><th width="240"></th><th></th></tr></thead><tbody><tr><td><code>Content-Disposition</code></td><td><code>attachment; filename=name_goes_here.docx</code></td></tr></tbody></table>

```
"payload": {},
"files": {
    "name_goes_here.docx": <GlyueFileHandle id=1 name=name_goes_here.docx>
}
```

Glyue's default filename `file` (with no extension) will be used if no name is specified in the request:

```
"files": {
    "file": <GlyueFileHandle id=1 name=file>
}
```
