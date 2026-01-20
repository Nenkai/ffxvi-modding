---
icon: material/animation
---

# :material-animation: Animations

Animations are stored in the `.anmb` format, which is also just a havok file, **with additional custom data inserted by SQEX at the bottom**.

They are usually found in the animation folder (in the case of characters), i.e `chara/c1001/animation/...`.

Battle animations are triggered by certain [Chara Timelines](../timelines/chara_timelines.md) elements.

!!! warning

    This is still very early and may not be fully functional.

    The custom data is currently dropped when exporting to .gltf.

### :material-export: `.anmb` -> `.gltf`

Use MdlConverter as such:

```
MdlConverter.exe <path to .anmb file> <path to skl file>
```

!!! warning

    **Reminder**: Currently the tool supports havok files up to v2018 and FFXVI uses v2020, so some models may not convert successfully due to additional unsupported data added in 2020.

### :material-import: `.gltf` -> `.anmb`

:material-arrow-right: Refer to [this guide](AnimationImportGuide.pdf) by CyberSoul.