<%*
let title = tp.file.title;
if (title.startsWith("Untitled")) {
  const newTitle = await tp.system.prompt("Name des PCs?");
  await tp.file.rename(newTitle);
  title = newTitle;
}
const gmPcPath = `Onaris/Spoiler/PCs`
const gmDescriptionPath = `Onaris/Spoiler/PCs/${title}-description`;
const gmBackstoryPath = `Onaris/Spoiler/PCs/${title}-backstory`;

if (!(await tp.file.exists(gmDescriptionPath + ".md"))) {
  await tp.file.create_new(tp.file.find_tfile(`Templates/PC/pc-template-description`), `${title}-description`, false, gmPcPath);
}
if (!(await tp.file.exists(gmBackstoryPath + ".md"))) {
  await tp.file.create_new(tp.file.find_tfile(`Templates/PC/pc-template-backstory`), `${title}-backstory`, false, gmPcPath);
}

tR += "---\n"
let tag = await tp.system.prompt("Weitere tags hinzufügen? Müssen mittels Leerzeichen getrennt werden.")
tR += "tags: " + "pc " + tag + "\n"
tR += "dg-publish: " + "true\n"

let klasse = await tp.system.prompt("Welche Klasse ist der Charakter?")
tR += "klasse: " + klasse + "\n"

let date = tp.date.now()
tR += "date: " + date + "\n"
tR += "---\n"

let player = await tp.system.prompt("Spielername?")
tR += "**Spieler:** [[" + player + "]]\n"

let campaign = await tp.system.prompt("Zu welcher Kampagne gehört der PC?")
tR += "**Kampagne:** [[" + campaign + "]]\n"

let group = await tp.system.prompt("Zu welcher Gruppe gehört der PC?")
tR += "**Gruppe:** [[" + group + "]]\n"

let str = await tp.system.prompt("Strength?")
let dex = await tp.system.prompt("Dexterity?")
let con = await tp.system.prompt("Constitution?")
let int = await tp.system.prompt("Intelligence?")
let wis = await tp.system.prompt("Wisdom?")
let char = await tp.system.prompt("Charisma?")

tR += "\n"
tR += "| STR | DEX | CON | INT | WIS | CHAR |\n";
tR += "| --- | --- | --- | --- | --- | ---- |\n";
tR += `| ${str} | ${dex} | ${con} | ${int} | ${wis} | ${char} |\n`;

tR += `## Beschreibung

### DM-Notes
![[${gmDescriptionPath}]]  
  
## Hintergrund  

### DM-Notes
![[${gmBackstoryPath}]]`;
%>

## Wird erwähnt in

```dataview
table file.name as "Datei"
from ""
where contains(file.outlinks, this.file.link)
```
