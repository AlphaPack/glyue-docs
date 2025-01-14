# Permissions

A Glyue user's permissions a governed by three concepts:

* [User Type (Standard, Staff, Service Account)](./#user-type)
* [User Permissions](./#user-permissions)
* [Group Permissions](./#group-permissions)

### User Type

| Page             | Standard User        | Staff User           |
| ---------------- | -------------------- | -------------------- |
| Dashboard        | :white\_check\_mark: | :white\_check\_mark: |
| Bookmarks        | :white\_check\_mark: | :white\_check\_mark: |
| Run History      | :white\_check\_mark: | :white\_check\_mark: |
| Build            | :white\_check\_mark: | :white\_check\_mark: |
| Swagger API      | :white\_check\_mark: | :white\_check\_mark: |
| Schedule         | :white\_check\_mark: | :white\_check\_mark: |
| Vault            | --                   | :white\_check\_mark: |
| Migrate          | --                   | :white\_check\_mark: |
| View Changes     | --                   | :white\_check\_mark: |
| Invite           | --                   | :white\_check\_mark: |
| Admin (settings) | --                   | :white\_check\_mark: |

A **Standard Glyue** user account is appropriate for everyday users who are involved in the building, maintenance, or monitoring of integrations.&#x20;

A **Staff Glyue** user is equivalent to a system administrator. These users have access to additional pages, notably the _Invite_ page, which allows them to invite additional Standard and Staff users into Glyue, and the _Admin_ page, which controls settings for the Glyue environment.

A **Service Account** is an account created to manage third-party system access to integrations on Glyue. A Service Account is only meant to execute integrations, and cannot log into the Glyue UI, view or edit integrations, or invite other users. Learn more about service accounts here.

### User Permissions

Both Standard and Staff users can have their abilities augmented by being granted permissions specific to a particular action. These permissions must be granted by a member of Sandbox staff — reach out to support@sandboxbanking.com for help.

#### Integration Permissions

Each user — both Standard and Staff — must be explicitly granted permission to access integrations. This must be done for each integration. Typically this is handled by your Sandbox Solution Engineer — reach out to support@sandboxbanking.com for help.

Integrations come with four separate permission types: Read, Write, Execute, and Debug. Details on these can be [found here](../integration_configuration.md#integration-permissions).

### Group Permissions

Groups may have additional permissions granted to them. Any member of the group automatically receives these permissions when they become a member of a group, and the permissions are revoked if the user is removed from the group.

Permissions granted through a group are only additive to any existing permissions a user has.&#x20;

Groups and Group Permissions are typically managed by Sandbox — reach out to support@sandboxbanking.com for help.
