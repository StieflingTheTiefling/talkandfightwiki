<%*
let title = tp.file.title;
if (title.startsWith("Untitled")) {
  const newTitle = await tp.system.prompt("Titel für den NPC?");
  await tp.file.rename(newTitle);
  title = newTitle;
}
const gmNpcPath = `Onaris/Spoiler/NPCs`
const gmDescriptionPath = `Onaris/Spoiler/NPCs/${title}-description`;
const gmBackstoryPath = `Onaris/Spoiler/NPCs/${title}-backstory`;

if (!(await tp.file.exists(gmDescriptionPath + ".md"))) {
  await tp.file.create_new(tp.file.find_tfile(`Templates/NPC/npc-template-description`), `${title}-description`, false, gmNpcPath);
}
if (!(await tp.file.exists(gmBackstoryPath + ".md"))) {
  await tp.file.create_new(tp.file.find_tfile(`Templates/NPC/npc-template-backstory`), `${title}-backstory`, false, gmNpcPath);
}

tR += "---\n"
let tag = await tp.system.prompt("Weitere tags hinzufügen? Müssen mittels Leerzeichen getrennt werden.")
tR += "tags: " + "npc " + tag + "\n"

tR += "dg-publish: " + "true\n"

let date = tp.date.now()
tR += "date: " + date + "\n"
tR += "---\n"

let ort = await tp.system.prompt("Wo lebt der NPC?")
tR += "**Ort:** [[" + ort + "]]\n"

let faction = await tp.system.prompt("Zu welcher Gruppe gehört der NPC?")
tR += "**Fraktion:** [[" + faction + "]]\n"

// Schreibe den unteren Text mit eingebetteten Links
tR += `## Beschreibung 
![[${gmDescriptionPath}]]  
  
## Hintergrund  
![[${gmBackstoryPath}]]`;
%>

## Wird erwähnt in

```dataview
table file.name as "Datei"
from ""
where contains(file.outlinks, this.file.link)
```
