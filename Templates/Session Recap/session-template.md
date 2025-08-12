<%*
let title = tp.file.title;
if (title.startsWith("Untitled")) {
  const newTitle = await tp.system.prompt("Titel für den NPC?");
  await tp.file.rename(newTitle);
  title = newTitle;
}

tR += "---\n"
let tag = await tp.system.prompt("Weitere tags hinzufügen? Müssen mittels Leerzeichen getrennt werden.")
tR += "tags: " + "npc " + tag + "\n"

tR += "dg-publish: " + "true\n"

let date = tp.date.now()
tR += "date: " + date + "\n"
tR += "---\n"

// Schreibe den unteren Text mit eingebetteten Links
tR += `## Beschreibung 
![[${gmDescriptionPath}]]  
%>
