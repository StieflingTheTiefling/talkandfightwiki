<%*
  let title = tp.file.title
  if (title.startsWith("Untitled")) {
    title = await tp.system.prompt("Title");
    await tp.file.rename(`${title}`);
  } 
  tR += "---"
%>

<%*
let tag = await tp.system.prompt("Weitere tags hinzufügen? Müssen mittels Leerzeichen getrennt werden.")
tR += "tags: " + "session-notes " + tag + "\n"

let date = tp.date.now()
tR += "date: " + date + "\n"
tR += "---"
%>

## Beschreibung
