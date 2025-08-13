---
dg-publish: true
tags:
  - oneshot/mirrarfestival
  - overview
---
# Spielercharaktere
```dataview
TABLE file.name AS "Datei"
FROM ""
WHERE contains(file.tags, "#oneshot/mirrarfestival") AND contains(file.tags, "#pc")
```
# Nichtspielercharaktere
```dataview
TABLE file.name AS "Datei"
FROM ""
WHERE contains(file.tags, "#oneshot/mirrarfestival") AND contains(file.tags, "#npc")
```
# Fraktionen
```dataview
TABLE file.name AS "Datei"
FROM ""
WHERE contains(file.tags, "#oneshot/mirrarfestival") AND contains(file.tags, "#fraktion") AND !contains(file.tags, "#pc")
```
