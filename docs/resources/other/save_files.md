---
icon: material/content-save
---

# :material-content-save: Save Files

Saves are saved as binary, no steam id check, encrypted & hash checked.

* [FF16Tools](https://github.com/Nenkai/FF16Tools) can unpack and repack them.
* [FF16Tools.Files](https://github.com/Nenkai/FF16Tools/tree/master/FF16Tools.Files/Save) - relevant library code.
* [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FaithSaveFile_Sub.bt)

## XML

It is possible to serialize/deserialize saves as XML. Simply hook the following signature and change `asXml` to true. The XML will be within the png file, after unpack.

Signature (ffxvi.exe, steam, 1.0.1):

### Serialization
* `sub_140796D58 - SerializeSave(__int64 a1, __int64 a2, __int64 a3, char* fileName, bool asXml)` 
```
48 89 5C 24 ? 55 56 57 48 81 EC ? ? ? ? 48 8B 05 ? ? ? ? 48 33 C4 48 89 84 24 ? ? ? ? 48 89 91
```

### Deserialization
* `sub_140796C94 - DeserializeSave(__int64 a1, __int64 a2, char* fileName, bool asXml, __int64 a5)` 
```
48 89 5C 24 ? 55 56 57 48 81 EC ? ? ? ? 48 8B 05 ? ? ? ? 48 33 C4 48 89 84 24 ? ? ? ? 48 8B AC 24
```