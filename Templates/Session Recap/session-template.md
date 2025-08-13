<%*
let title = tp.file.title;
if (title.startsWith("Untitled")) {
  const newTitle = await tp.system.prompt("Titel für den Recap?");
  await tp.file.rename(newTitle);
  title = newTitle;
}
const gmSessionPath = `Onaris/Spoiler/Recap`
const gmDescriptionPath = `Onaris/Spoiler/Recap/${title}-spoiler`;

if (!(await tp.file.exists(gmDescriptionPath + ".md"))) {
  await tp.file.create_new(tp.file.find_tfile(`Templates/Recap/session-template-spoiler`), `${title}-spoiler`, false, gmSessionPath);
}

tR += "---\n"
let tag = await tp.system.prompt("Für Welche Kampagne ist der Recap?.")
tR += "tags: " + "session-recap " + tag + "\n"

tR += "dg-publish: " + "true\n"

let date = tp.date.now()
tR += "date: " + date + "\n"
tR += "---\n"

// Schreibe den unteren Text mit eingebetteten Links
tR += `## Beschreibung 
![[${gmDescriptionPath}]]`;  
%>

