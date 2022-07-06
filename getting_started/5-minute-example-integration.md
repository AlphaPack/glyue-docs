---
description: Email Notification Integration Example
---

# 5-Minute Example Integration

## Topic 1 - Building Your First Integration

1. Sign into Glyue
2. Select _**Build**_ from the left dialog
3. This should take you to an empty build page
4. Ensure you are on the _Integration_ option for the Component dropdown
5. Click _**Add Row** at_ the bottom of the page
6. This will create a new row in the integration table
   1. For our first integration, put anything you like in for the _Path Name_ and _Description_ fields
   2. Ensure _Run Async_ and _Http Api are_ set to **true**
7. Click _**Save** at_ the bottom of the page
8. You’ve just created your first integration!

## Topic 2 - Running Your new Integration

{% hint style="info" %}
At this point, you should have an integration built that doesn't do anything but run asynchronously and is accessible as an HTTP API endpoint. If you don't, please complete Topic 1 above.
{% endhint %}



1. We want to run the new integration we just created in Topic 1, but how?
   1. Let’s try running your integration from _**Swagger API** _ found in the left dialog of Glyue
      1. Select the integration you created from the **default** list. It should be in a green box labeled with the Path Name you specified when you created the integration like this: _/your\_integration\_path\_name_
      2. Click _**Try it out**_ in the top right of the integration dialog
      3. Click _**Execute** (don’t worry about the request body, for now, we will go over that in the next topic)_
   2. Once executed let’s see what happened with _**Run History** _ found in the left dialog
      1. It failed?? Why? Didn’t we set up the integration correctly? There wasn’t anything in the integration to make it fail, right? Let’s investigate the run by clicking on the run → FAILURE and looking at the _Stack Trace_ provided by Glyue for the failure.
      2. It looks like there was an issue with the integration config:
         1. _django\_glyue\_app.models.IntegrationConfig.DoesNotExist: IntegrationConfig matching query does not exist_
      3. It appears we forgot to set up a config for our new integration! Setting these up is crucial in being able to run and test the integrations you are building, so let’s do that!
2. To create an integration config, navigate to _**Admin**_ in the left dialog
3. Click into _**Integration Config**_
4. Once on the Integration Config page, click _**Add Integration Config** _ on the top right of the page
5. Once in the Add Integration Config page select the integration you created from the **Integration** dropdown
   1. Uncheck _Email digests_
   2. Check _Store payloads in run history_
   3. Click **Save** in the bottom right of the page
6. The integration config has been created! Let’s try running the integration again through _**Swagger API**_
7. After clicking _**Execute**_ navigate to _**Run History**_ to check the **Run History**!
   1. It didn’t fail, right? That’s great news! Your integration is officially running and testable!
   2. Investigate the INPUT and OUTPUT for the run
      1. For INPUT you should see one line with “string” in it
      2. For OUTPUT you should see this:
      3. If you don’t see this or see \*REDACTED\* for both INPUT and OUTPUT, ensure that _Store payloads in run history_ is checked in the integration config!
8. You've just run your first integration!
