---
icon: material/map
hide:
  - toc
---

# :material-map: Gamemap

Gamemaps are the levels in the game.

!!! note
    This table was generated with the following pseudo-query:

    ```sql
    SELECT gamemap.Key, placename.Name, gamemap.MapFile
    FROM gamemap
    LEFT JOIN placename ON gamemap.PlaceNameId = placename.Key;
    ```

If you need to find a specific map, ++ctrl+f++ and search by name (there may be more than 1 result).

{{ read_csv('gamemap_ids.csv') }}