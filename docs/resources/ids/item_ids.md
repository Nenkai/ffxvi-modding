---
icon: material/sack
---

# :material-sack: Item IDs

General item ids. For equippable items, refer to [this page](equip_item_ids.md).

!!! note
    This table was generated with the following pseudo-query:

    ```sql
    SELECT Key, Name FROM item;
    ```

If you need to find a specific item, ++ctrl+f++ and search by name (there may be more than 1 result).

{{ read_csv('item_ids.csv') }}