# Integration Builder Page

## Main Toolbar

Buttons on the Integration Builder Toolbar enables users to add, duplicate and clear changes within the Builder. The special tool, `deep clone` creates a full copy of the entire Builder Row selected, and all of the children associated with it.

<figure><img src="../.gitbook/assets/glyue_toolbar_20221024.png" alt=""><figcaption></figcaption></figure>

## Filters

### Column

The column filter handles the display status of the Build Page. By default, all columns are shown but each column can be toggled to be hidden.

### Filter

The filter feature highlights matched Builder Rows based on the entered values. It will search in real-time and provide the number of results returned within the button.

### SQL Filter

This performs the back-half of a SQL filter for the table. This allows users to search with higher specificity than the traditional text based filter.

Example Filters

```
FROM * SELECT
```

### Comments

Comments are the main source of communication when jointly working within the Integration Builder. Comments can be created by anyone who has read-access to the integration.

### Tags

Each section of the Integration Builder has the ability to add a `tag` to Builder rows. This provides a way to identify specific pieces of an integration and how they relate. It is particularly helpful when used in combination with Bookmarks.



## Find and Replace

<figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

The Find and Replace toolbox offers a powerful way to quickly search for and update text within the cells on the build page. It will only search through visible cells.

1. The text to find.
2. The replacement text, if replacing.
3. Number of matches, by cell. Multiple instances of the text in one cell counts as one.
4. Move forward/backward through the matches. _Enter_ and _shift-Enter_ can also be used to move forward and backward respectively.
5. Replace the currently highlighted instance
6. Replace all found instances. If (11) _Replace within Selection_ is enabled, will only replace the matches within the selected cells.
7. When enabled, hides all rows that do not have a match.&#x20;
8. When enabled, looks for an exact case (case sensitive) match.
9. When enabled, only counts whole words as matches (e.g. "banker" will not match "bank").
10. When enabled, interprets the "find" text as a regular expression.
11. When enabled, _Replace All_ will only replace matches within the selected cells.&#x20;
