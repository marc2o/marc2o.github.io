---
layout: article
language: de-DE
image: /images/...
title: Schreiben in Markdown
author: marc2o
---

Mittlerweile nutze ich [John Grubers Markdown](https://daringfireball.net/projects/markdown/) schon seit gut zehn Jahren. Schön, dass es in jedem Text-Editor geht, aber ich mag es minimal und elegant.

Markdown-Editoren:
* **[Byword](https://bywordapp.com)** (4,7 MB)
* **[iA Writer](https://ia.net/de/writer)** (22,5 MB)
* **[Mark Text](https://marktext.app)** (289,9 MB)
* **[Nota](https://nota.md)** (203,0 MB)
* **[Typora](https://www.typora.io)** (31,6 MB)
* **[Zettlr](https://zettlr.com)** (380,0 MB)

Außer Konkurrenz:
* [Visual Studio Code](https://code.visualstudio.com/) (278,1 MB)

## Mein Visual Studio Code-Setup

Ich mag den iA-Font, ich hab die Schrift beim Schreiben von Text gern größer und Umbruch ist Pflicht. Außerdem darf der Cursor sanfter blinken. Auf macOS sieht der Abschnitt meiner settings.json so aus:

```json
"[markdown]": {
    "editor.wordWrap": "on",
    "editor.renderWhitespace": "all",
    "editor.quickSuggestions": false,
    "editor.fontFamily": "iA Writer Duospace",
    "editor.fontSize": 17,
    "editor.cursorBlinking": "phase",
    "editor.links": true
},
```
Auf meinem mobilen Arbeitsrechner mit Windows habe ich den Umbruch anders definiert, weil die Zeilen beim Umbruch am Fensterrand zu lang werden.

```json
"editor.wordWrap": "wordWrapColumn",
"editor.wordWrapColumn": 80,
```

Notizen: https://www.maketecheasier.com/best-markdown-editors-for-macos/