# 1. Integration Setup

**Creating the Integration**

\
The first step to building a Customer360 retrieval API would be to create a new row on the integration table of the build page.\
\
Navigate to the Build page and change the current component to the **Integration** option.

<figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>

\
Once there, press the "Add Row" button to create the integration. You'll need to provide a **Path Name** as well as a **description** in order to save the added integration using the save button on the bottom of the screen.\


**Configuring the Integration**\
\
&#xNAN;_&#x54;o complete this step, you'll need access to the Glyue Admin Page._\
\
Navigate to the Admin Page using the panel on the left hand side of the screen. Scroll down until you find the configuration item labelled "Integration Configs" and click the "Add New" button next to it.\
\
Choose the appropriate integration name that you created earlier and choose the settings you'd like configured for this integration. We recommend checking the "Store payloads in run history" box in order to properly trace the data when building and using the integration.\
\
From here, scroll down the left pane until you find the configuration item labelled "Adapter Configs: CodeConnect IB&#x53;**"** and add a new item. \
\
&#xNAN;_`If you are building an integration to a different CodeConnect core, choose the appropriate item; i.e. "Adapter Configs: CodeConnect Horizon" for the Horizon core.`_\
\
Fill in the corresponding credentials on the configuration page. You'll need to reference your CodeConnect portal or reach out to your FIS account representative for access to some of this information.

<figure><img src="../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>

Once completed, scroll down the left pane until you find the configuration item labelled "Adapter Config Bindings" and add a new item. Choose the corresponding integration that you just created and the Adapter Config you just created and click save. This step essentially assigns the **Integration** to use the adapter configuration information we just provided when interacting with the core.
