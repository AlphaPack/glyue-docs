# Integration Life-Cycle

<figure><img src="https://lucid.app/publicSegments/view/23d1c801-dc73-4a48-b05d-72cd0ebe95b7/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://lucid.app/publicSegments/view/2fd4559a-e358-4415-a695-a19d53626ac2/image.png" alt=""><figcaption><p><a data-mention href="integration_components/">integration_components</a></p></figcaption></figure>

<figure><img src="https://lucid.app/publicSegments/view/cb609b9c-a199-4adc-8521-0abecdc4aa3b/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://lucid.app/publicSegments/view/ff90e49c-d8d8-43bd-b3a9-ad0c14a7e23c/image.png" alt=""><figcaption></figcaption></figure>

## **How an Integration is called:**

#### Externally:

An integration can be called from an exposed API path, as defined within the webservice or the integration path\_name. The payload will be parsed from the associated request, by default the HTTP request body.

#### Internally

* Within the lifecycle of another integration with the [#callint](special\_functions.md#callint "mention") special function.
* Based on a scheduled `cron` job, given admin permissions.

