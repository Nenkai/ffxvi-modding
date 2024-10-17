---
icon: material/account-badge
---

# :material-account-badge: ENpc Ids

Enpc Ids are event (?) entities in the game.

!!! warning
    Only rows that have a valid link to `speaker` are included, not all rows are present.

!!! note
    This table was generated with the following query:

    ```sql
    SELECT enpcbase.Key, speaker.Name
    FROM enpcbase
    INNER JOIN speaker ON enpcbase.SpeakerId = speaker.Key;
    ```

If you need to find a specific entity, ++ctrl+f++ and search by name (there may be more than 1 result).

{{ read_csv('enpc_ids.csv') }}