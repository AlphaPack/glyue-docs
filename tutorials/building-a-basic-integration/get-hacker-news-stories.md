# 4. Get Story Content

We have communicated with the Hacker News API, but its response contains a list of story ids while we need the URLs for our email digest. Let’s make another request (or rather, a set of requests) to retrieve each story by its id so we can later collate their URLs into a single message.

#### Service Request: `get_story_by_id` <a href="#step5-gethackernewsstories-servicerequest-get_story_by_id" id="step5-gethackernewsstories-servicerequest-get_story_by_id"></a>

1. From the **Build** page, with **Integration** selected under Component, right-click our integration and click **Go To > Service Request**.
2. Add a new row, enter the following, and save:
   * **Sequence:** `100`
   * **System:** `HTTP`
   * **Service Name:** `n/a`
   * **Formula Variable:** `get_story_by_id`
   *   **Call For Each:** copy and paste the Python code below.\
       This expression evaluates to the list of ids we got from `get_story_ids`, then cut off at the `limitQuery` value (if provided). It’s ok if this code doesn’t make sense yet, so don’t worry!

       ```
       get_story_ids.response.payload.unwrap()[:input.payload.limitQuery or None]
       ```

Glyue will execute a SR once for every item in its **Call For Each**. Using python lists is the most common.

#### Field Mappings for `get_story_by_id` <a href="#step5-gethackernewsstories-fieldmappingsforget_story_by_id" id="step5-gethackernewsstories-fieldmappingsforget_story_by_id"></a>

1. Right-click the `get_story_by_id` SR and select **Go To > Field Mapping**.
2. Click **\[➕ADD ROW]** 2 times to get 2 blank rows. Enter the following values and then save:
   * First row
     * **Field:** `url_path`
     * **Value:** `f"/v0/item/{sritem}.json"`
     * **Value Type:** `str`
   * Second row
     * **Field:** `method`
     * **Value:** `"GET"`
     * **Value Type:** `str`

`sritem` is a special variable that represents the current item in the **Call For Each** of its parent SR. In this case, `sritem` will be a story id.

#### Test `get_story_by_id` <a href="#step5-gethackernewsstories-testget_story_by_id" id="step5-gethackernewsstories-testget_story_by_id"></a>

1.  Navigate to the **Run History** page (or open it in a new tab to keep it handy!) and re-run the integration with this input payload:

    ```
    {
      "email": "user@email.net",
      "limitQuery": 10
    }
    ```
2. It should complete successfully. Wait for the most recent run to appear at the top of the **RUNS** column and click it to see its **STEPS** in the middle column. We should see several records now- an INPUT, the first REQUEST (`get_story_ids`), but after that there should be 10 more REQUEST records labelled with `get_story_by_id`. Click one of them to view its request and response payloads, which should look something like this:
   *   REQUEST

       ```
       {
           "service_name": "n/a",
           "payload": {
               "url_path": "/v0/item/36712566.json",
               "method": "GET"
           },
           "sub_requests": {}
       }
       ```
   *   RESPONSE

       ```
       {
           "success": true,
           "payload": {
               "by": "JoeMayoBot",
               "descendants": 0,
               "id": 36712566,
               "score": 1,
               "time": 1689268222,
               "title": "Windows 95, 98, and other decrepit versions can grab online updates again",
               "type": "story",
               "url": "https://arstechnica.com/gadgets/2023/07/windows-95-98-and-other-decrepit-versions-can-grab-online-updates-again/"
           },
           "messages": []
       }
       ```

{% hint style="success" %}
Our Glyue integration has now made 11 requests to an external API, with 10 of them being done in a programmatic fashion. Nice Job!
{% endhint %}
