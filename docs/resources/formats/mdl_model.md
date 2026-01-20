---
icon: simple/hackthebox
---

# Model

!!! warning

    Needs more info.

Overview of contents:

* Vertex/Index buffers separately, up to 8 (1 for each LOD, 8 LODs max). compressed with DirectStorage
* Vertex layout declarations (set + attributes)
* List of material files to load (.mdl), linked to the model
* Boundary Box
* (Optionally) two additional compressed buffers, purpose unknown

And then:

* LOD Infos (vertex/tri count)
* Mesh Infos
* Material References
* Draw Calls (?)
* Joints
* Face Joints
* Muscle Joints
* Unknown joint parameters
* Additional Parts (addressed by PartAdditionalDataParam Nex table)
* Options (addressed by ModelCoordinate Nex table)
* VFX Entries (purpose unknown)
* Unknown entries
* Unknown entries (#2)
* 'MCEX' section (external content?) - purpose unknown
* Joint Bounds
* Joint Max Bounds
* Unknown entries (#3)