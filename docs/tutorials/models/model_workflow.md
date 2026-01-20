---
icon: simple/hackthebox
---

# :simple-hackthebox: Model Workflow

!!! note

    This page only provided for modding purposes, not ripping purposes.

    This page may be missing information. It was written by someone only familiar with the tools, not 3D Modeling.

Requirements:

* :material-tools: [FF16-Model-Importer](https://github.com/Nenkai/FF16-Model-Importer)
* :material-blender-software: Blender. The workflow is centered around Blender as a whole.

It may be worthwhile to check out the dedicated [Model](../resources/formats/mdl_model.md) format page to get an understanding of what is in there.

---

## Models
### :material-export: `.mdl` to `.gltf`

Drag any `.mdl` file into the executable for it to create a folder containing `.gltf` files for all 8 LODs.

The format has no mesh names therefore they're taken from the material that they reference.

!!! warning "Armature"

    There will be no armature in the case of rigged models. The skeleton is stored in a separate file, contained in a separate pack per model. 
    
    Example: `chara/c1001/c1001.pac` -> `animation/chara/c1001/skeleton/<body/face/hair/>/<body/face/hair/>.skl`

    The tool supports this, provide the path to model aswell as the pac file and run this in a command prompt and run: 
    
    ```
    MdlConverter.exe <path to .mdl file> <path to .pac file>
    ```

    Skeleton files are stored in a [Havok](https://www.havok.com/) format (version `2020_2_0_r1`). Currently the tool supports up to 2018, so some models may not convert successfully due to additional unsupported data added in 2020.

!!! note "Note: Custom Attributes (click to expand)"
    
    There may be per-vertex custom data. The tool currently puts them in custom GLTF attributes starting with `_`.

    You can access these by selecting a mesh in Blender, heading to the `Data` tab on the right side, and `Attributes`. From there you can head into Vertex Paint mode.

    The `_COLOR_0` is not put inside `COLOR_0` as it uses the alpha channel that Blender 4.1 drops. It appears to be used as wrinkles data in the case of face models.

---

### :material-import: `.gltf` to `.mdl`

#### :material-blender-software: Blender Export Settings

**Make sure the following options are enabled, very important!**

* `Data`
    * `Mesh`
        * Tangents
        * **Attributes**
    * `Vertex Colors`
        * Use Vertex Color (Active)
        * Export All Vertex Colors

Strongly recommended to leave this as default for FFXVI.

#### Converting

To convert back to `.mdl`, you need the original folder, **aswell as the original file**.

The tool will use the original `.mdl` as a base for all the data, such as the joints, vfx data, etc.

Upon building, the tool will clear ALL of the following:

* LODs
* Meshes
* Vertex/Index buffers
* Vertex layout Attributes

Everything else will be preserved from the original model specified.

---

## Animations

:material-arrow-right: Continue on to the [Animations](animations.md) page.