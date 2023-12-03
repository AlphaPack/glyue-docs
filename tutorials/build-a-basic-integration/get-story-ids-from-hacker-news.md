# Get Story Ids from Hacker News

Now we are ready to create our first external API call. Integrations can have any number of calls. In Glyue these calls are referred to as **Service Requests (SRs)**. Each SR represents one API call, and will take a set of **Field Mappings** (more on this later) as input data for sending to the other system. When it executes, it will send the data and save the response.

In order to know how to compose a Service Request and its Field Mappings for any system, the user will need both the respective Glyue adapter documentation, as well as any documentation of the external system. The adapter reference article will lay out the Adapter Config, Service Request, and Field Mapping requirements, while the other system’s documentation should inform the user as to what endpoints are available, what each endpoint expects and returns, error troubleshooting advice, etc.

{% content-ref url="../../reference/adapters/" %}
[adapters](../../reference/adapters/)
{% endcontent-ref %}

#### Service Request: `get_story_ids` <a href="#step4-getstoryidsfromhackernews-servicerequest-get_story_ids" id="step4-getstoryidsfromhackernews-servicerequest-get_story_ids"></a>

In our first SR, we want to query Hacker News for the latest stories.

1. From the **Build** page, with the Component set to **Integration**, right click the integration and click **Go To > Service Request**.
2. Click the **\[➕ADD ROW]** button, and provide these values:
   * **Sequence:** `0`
   * **System:** `HTTP` (this is how we indicate that the SR should use the HTTP adapter)
   * **Service Name:** `n/a`
   * **Formula Variable:** `get_story_ids`
3. Leave the rest of the row unchanged and save.

#### Add Field Mappings for SR: `get_story_ids` <a href="#step4-getstoryidsfromhackernews-addfieldmappingsforsr-get_story_ids" id="step4-getstoryidsfromhackernews-addfieldmappingsforsr-get_story_ids"></a>

Now we’re ready to tell the Service Request what data to send using **Field Mappings (FMs)**. An SR can have any number of FMs. Each FM represents a field in the data that will be sent to the other system, as well as its value (or the logic by which the value is gotten).

Now we’re going to add a couple of simple FMs to our SR.

1. From the **Build** page with Component set to **Service Request**, right click the SR we just created and select **Go To > Field Mapping**.
2. Click **\[➕ADD ROW]** 2 times to add 2 new rows.
3. In the top row add the following:
   * **Sequence:** `0`
   * **Field:** `url_path`
   * **Value:** `"/v0/newstories.json"` (include the quotes)
   * **Value Type:** `str`
4. For the next row, enter:
   * **Sequence:** `0`
   * **Field:** `method`
   * **Value:** `"GET"` (include the quotes)
   * **Value Type:** `str`
5. Save.

#### Test `get_story_ids` <a href="#step4-getstoryidsfromhackernews-testget_story_ids" id="step4-getstoryidsfromhackernews-testget_story_ids"></a>

We are now ready to send our first request to an external real API! Let’s test the integration:

1. Go to the **Run History** page, and re-run our integration with valid inputs.
2. Wait for this run to appear in the **RUNS** column, then click it.
3. In the middle **STEPS** column, there should now be 3 records: INPUT, REQUEST, and OUTPUT. Select the REQUEST.
4.  The collapsible `⟶ Request` and `⟵ Response` sections should appear on the right, along with their payloads. The request should look like this:

    ```
    {
        "service_name": "n/a",
        "payload": {
            "url_path": "/v0/newstories.json",
            "method": "GET"
        },
        "sub_requests": {}
    }
    ```

    While the response will look something like this:

    ```
    {
        "success": true,
        "payload": [
            36688166,
            36688146,
            36688107,
            36688074,
            ...
        ],
        "messages": []
    }
    ```

Congratulations! The integration has successfully communicated with an external system!
