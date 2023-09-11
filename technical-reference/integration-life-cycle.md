# Integration Life-Cycle

<figure><img src="https://lucid.app/publicSegments/view/e19d786f-9bd6-4767-bed1-edad72bc275d/image.png" alt=""><figcaption><p>Overview of how the layers of the Build table flow into one another</p></figcaption></figure>

<figure><img src="https://lucid.app/publicSegments/view/645904be-6d3f-4f85-b19e-419efaf1d684/image.png" alt=""><figcaption><p>Integration process diagram</p></figcaption></figure>

<figure><img src="https://lucid.app/publicSegments/view/fb8f616a-bb81-4532-b689-5031576c22dc/image.png" alt=""><figcaption><p>Service Request process diagram</p></figcaption></figure>

<figure><img src="https://lucid.app/publicSegments/view/a71af81d-7449-4299-b90f-6af82a7f27b5/image.png" alt=""><figcaption><p>Service Call process diagram</p></figcaption></figure>

<figure><img src="https://lucid.app/publicSegments/view/700e0d55-76f7-4e3c-958a-00fbd10b0940/image.png" alt=""><figcaption><p>Field Mappings process diagram</p></figcaption></figure>

## **How an Integration is called:**

#### Externally:

An integration can be called from an exposed API path, as defined within the webservice or the integration path\_name. The payload will be parsed from the associated request, by default the HTTP request body.

#### Internally

* Within the lifecycle of another integration with the  special function.
* Based on a scheduled `cron` job, given admin permissions.
