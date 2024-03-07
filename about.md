---
layout: article
title: Hallo, Welt.
author: marc2o
language: de-DE
image: /images/marc2o-r66.jpg
---

Hier folgt ein kleiner Einblick in das was mich um- und antreibt, wo ich herkomme und hinwill. In Schlüssel&shy;begriffen. Ohne Anspruch auf Vollständigkeit oder besondere Reihenfolge.

**Für Augen und Ohren.**

<style>
	.data_items {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: baseline;
		flex-shrink: 1;
		gap: 1rem;
	}
	.data_item {
		display: inline-block;
		height: auto;
	}
	.data_item .cover {
		overflow: hidden;
		border-radius: 0.2rem;
	}
	.data_item img {
		display: block;
		object-fit: cover;
		width: 100%;
	}
	.data_item span {
		display: block;
		padding: 0.5rem;
	}
	.album {
		width: 15rem;
		aspect-ratio: 1/1;
	}
	.book {
		width: 12rem;
		aspect-radio: 2/4;
	}
</style>
<div class="data_items">
	{% for item in site.data.items %}
  <div class="data_item {{items.type}}">
    <div class="cover"><img src="{{items.img}}" alt="{{items.type}} cover"></div><span>{{items.name}}, {{items.by}}</span>
  </div>
  {% endfor %}
</div>

**Hannover.**
Dieses Kleinod niedersächsischer Tristesse an der Leine. Einst neunte Kur, dann Königreich. Angeblich Hauptstadt des Mittelmaßes. Auf jeden Fall Landeshauptstadt. Von Niedersachsen. Zwischendurch Welthauptstadt. Während der EXPO 2000. Für böse Zungen auch einfach die wahrscheinlich größte Autobahn­raststätte der Welt. Hannover liegt nicht am Arsch der Welt. Aber man kann ihn von dort aus sehen. Heißt es. Für mich ist Hannover Heimatstadt im Grünen, mit vielen blauen Seen, zwei Flüssen und einem roten Faden.

**Internet.**
Für den einen Bibliothek, für den anderen Bühne. Für mich kreativer Raum und Informations­quelle. Schon seit 1997. Als noch das gesamte Netz _social_ war und der Begriff »Webdesign« noch nicht erfunden schien. Mit GeoCities und echten Blogs. Die Verweildauer im Netz war kürzer, so ohne Flatrate. Und auch langsamer. So über Ortsnetz und Studiserver. Umso größer war die Freude, wenn jemand zeitgleich bei ICQ online war. Vielleicht hat auch deshalb damals kaum jemand Zeit verschwendet für Hasskommentare und Fake-News. Manchmal fehlt mir das Netz von früher, so unreguliert und unästhetisch, wie es war. Ohne selbst&shy;darsteller&shy;ische Besserwisser (alias _Influencer_) und Cookie-Consent-Banner.



**Kurzübersicht.**

- Linkshänder
- Sonntagskind
- Träumer
- Katzenpapa
- Autodidakt
- Promovierter Linguist
- eher Astronom als Astronaut
- Kind der Heimcomputer-Revolution
- Bücherliebhaber
- Musik-Amateur im barocken Sinne des Wortes
- mag kleine Instrumente (Ortega Konzert-Ukulele und AKAI MPK mini Play)
- Atari- & Nintendo-Konsolen
- Commodore- und Apple-Computer
- früher 68k-Asm, Forth und Java
- heute Lua, C und JavaScript
- (Fortsetzung folgt. Vielleicht.)
