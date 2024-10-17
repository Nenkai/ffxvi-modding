---
icon: material/account-badge
---

# :material-account-badge: BNpc Ids

Bnpc Ids are general entities in the game.

!!! warning
    Only rows that have a valid link to `speaker` are included, not all rows are present.

!!! note
    This table was generated with the following query:

    ```sql
    SELECT bnpcbase.Key, speaker.Name
    FROM bnpcbase
    INNER JOIN speaker ON bnpcbase.SpeakerId = speaker.Key;
    ```

If you need to find a specific entity, ++ctrl+f++ and search by name (there may be more than 1 result).

{{ read_csv('bnpc_ids.csv') }}