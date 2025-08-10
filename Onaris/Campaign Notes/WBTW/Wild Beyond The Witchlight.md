---
dg-publish: true
tags:
  - overview
  - kampagne/witchlight
---
# Spielercharaktere
```dataview
TABLE file.name AS "Datei"
FROM ""
WHERE contains(file.tags, "#kampagne/witchlight") AND contains(file.tags, "#pc")
```
# Nichtspielercharaktere
```dataview
TABLE file.name AS "Datei"
FROM ""
WHERE contains(file.tags, "#kampagne/witchlight") AND contains(file.tags, "#npc")
```
# Fraktionen
```dataview
TABLE file.name AS "Datei"
FROM ""
WHERE contains(file.tags, "#kampagne/witchlight") AND contains(file.tags, "#fraktion" AND !contains(file.tags, "#pc"))
```
