# Migrate an Integration

When developing integrations, Sandbox Banking Solution Engineers utilize separate `DEV` and `PROD` environments to write code and test changes before deploying that code to a production environment.&#x20;

When changes to an integration are ready to be deployed to the `PROD` environment, Glyue provides two features that facilitate the process:

* The _Migrate_ page
* The _View Changes_ page

### Migrate

The _Migrate_ page (pictured below) allows a user to select integrations from a source environment (often, the `DEV` environment) to be migrated into the destination system (the current logged-in environment, often `PROD`).&#x20;

<figure><img src="../.gitbook/assets/image (106).png" alt=""><figcaption><p>The Migrate page in Glyue, showing multiple source environments and the integrations present in each environment</p></figcaption></figure>

If an integration has multiple changes ongoing, Glyue affords the option to select specific portions of that integration to migrate, rather than migrating the entire integration. This can be useful for deploying smaller fixes while a larger piece of work is still ongoing.

If the whole integration is to be migrated, simply select the integration and click _PERFORM MIGRATION._&#x20;

### View Changes

Portions of the integration can be selected by selecting _VIEW INCOMING CHANGES_ . This opens the _View Changes_ page, showing the differences between the incoming (new) integration and the current version of the integration.

Using the _Migrate_ column, you can select the rows you wish to include in the migration. In the example below, four Field Mappings have been selected, while the rest will remain untouched.

<figure><img src="../.gitbook/assets/image (107).png" alt=""><figcaption><p>The interface reviewing the specific rows selected for a migration.</p></figcaption></figure>

By saving the selection of rows in to "Pull Request" using the _SAVE AS PR_ button, then returning to the _Migrate_ page, you can migrate your selection of rows, instead of the whole integration.

