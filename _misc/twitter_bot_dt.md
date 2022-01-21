---
title: "Kumulative Mitteltemperatur in Österreich"
excerpt: "<img src='/images/bot/tas_cummean_austria_2021_365_stepsize-auto_delay-40_size-1000.gif' width='40%'>"
collection: misc
permalink: /misc/twitter_bot_dt
---

<em>This post is only available in German. You can visit the bot on <a href="https://twitter.com/tas_to_date" target="_blank">Twitter</a> or have a look at the code on <a href="https://github.com/lukasbrunner/tas_to_date" target="_blank">GitHub</a>.</em>

Die Idee für dieses Projekt geht auf eine Diskussion um Ostern 2021 zurück. Wir konnten uns damals nicht einigen ob das Jahr in Österreich bisher besonders warm oder besonders kalt gewesen war. Um diese Frage zu beantworten schaue ich mir hier die Temperatur gemittelt über Österrreich und gemittelt vom 1. Jänner bis zu einem bestimmten Tag im Jahr an (also zum Beispiel on 1. Jänner bis Ostern). Ich vergleiche sie dann mit der Temperatur im selben Zeitraum in früheren Jahren.

Inzwischen schreiben wir 2022 und es ist möglich sich den Verlauf über ganz 2021 anzuschauen. In der daraus resultierenden Zeitreihe ist die Temperature an jedem Tag der zeitliche Mittelwert der Temperatur von 1. Jänner bis zu diesem Tag. Ich nenne das die **kumulative Mitteltemperatur**, angelehnt an das Konzept der kumulativen Summe (<a href="https://de.wikipedia.org/wiki/CUSUM" target="_blank">CUMSUM</a>).

Die kumulative Mitteltemperatur am 1. Jänner selbst ist also gleich der Tagestemperatur am 1. Jänner, während die kumulative Mitteltemperature am 31. Dezember gleich der Jährlichen Mitteltemperatur ist. Der Vergleich mit vergangenen Jahren ermöglicht eine aussage darüber ob das Jahr im Durchschnitt bisher unüblich warm oder unüblich kalt war. Ich verwende dafür zwei Metriken: die Abbweichung vom langjährigen Mittel (1950-2021) und den Rang.

Wie man in der Abbildung unten sehen kann war die kumulative Mitteltemperatur am 4. April 2021, dem Ostersonntag, um 1.1°C höher als im langjährigen Mittel und die 19. wärmste in den letzten 72 Jahren. Die richtige Antwort für die eingangs erwähnte Diskussion wäre also, dass das Jahr 2021 bis Ostern wärmer war als die meisten der 71 Jahre davor aber nicht zu den extremsten Jahren gehörte.

<img src="/images/bot/tas_cummean_austria_2021_094.jpg" width="90%">

Einige andere Sache, die bei der Abbildung oben sofort ins Aufg fällt ist, dass der graue Bereich mit fortschreitendem Jahr immer enger wird. Das ist eine konsequenz aus dem Mittelwert: am Anfang des Jahres wird nur über wenige Tage gemittelt, das heißt jeder zusätzliche Tag hat vergleichsweiße viel Einfluß, während am Ende des Jahres über 300+ Tage gemittelt wird, ein einzelner Tag daher kaum mehr einen Einfluss hat. Das kann man auch bereits für 2021 an der roten Linie erkennen: anfangs schwankt sie recht starkt aber ab circa März scheint sie sich einzupendeln und bleibt relativ stabil. Was man aus der Abbildung (Werte ganz rechts) ebenfalls erkennt ist, dass die Jährliche Mitteltemperatur in Österreich etwa 6°C ist, mit einer Schwankungsbreite von etwa &plusmn;2°C.

In diesem Kontext ist es natürlich interessan die kumulative Mitteltemperatur mit der täglichen Temperature zu vergleichen. Da wir diese jeden Tag subjektiv erleben beeinflusst sie unsere Wahrnehmung auch stärker als eine über Monate gemittelte Temperatur. Die Abbildung unten ist ähnlich zur letzten Abbildung, zeigt aber für jeden Tag einfach die Temperatur an diesem Tag.

<img src="/images/bot/tas_daily_austria_2021_094.jpg" width="90%">

Was man sofort erkennt ist die deutlich größere Schwankung, die -anders als für die kumulative Mitteltemperatur- übers Jahr nicht abnimmt. Bis Ostern hatte 2021 tatsächlich auch bereits 6 Tage, die einen neuen Temperaturerekord in Österreich aufgestellt hatten (in der Abbildung unden markiert). Gleichzeitig hab es aber auch drei Perioden mit Temperaturen deutlich unter dem langjährigen Mittel, eine kurz vor Ostern während der sogar ein neuer Kälterekord aufgestellt wurde. Es ist also vielleicht auch nicht verwunderlich wenn der einer oder die andere in unserer Diskussion zu Ostern den Eindruck hatte als wäre 2021 bisher sehr kalt gewesen.

Die Animation unten zeigt die Entwicklng der Tagesmitteltemperatur und kumulativen Mitteltemperatur in Österreich während 2021. Man sieht wie die tägliche Temperatur die kumulativen Temperatur anfangs stark beeinflusst, während der Einfluss gegen Ende des Jahres abnimmt aber. Aber gerade längere sehr warme Perioden wie zum Beispiel Mitte Juni können die kumulative Temperature weiterhin beeinflussen (in diesem Fall erhöhen). Im Jährlichen Mittel landet 2021 mit 0,8°C über dem langjährigen Mittwelwert (1950-2021) auf Rang 18/72.

<img src="/images/bot/tas_both_austria_2021_365_stepsize-auto_delay-40_size-1000.gif" width="90%">

<!-- https://www.zamg.ac.at/cms/de/klima/klima-aktuell/klimamonitoring/?param=t&period=period-y-2021&ref=3 -->

Der Einlfuss des Klimawandels
---

Ich habe mich in dieser Betrachtung der Temperatur in Österreich nicht explizit mit dem Klimawandel auseinandergesetzt. Aber implizit spielt er natürlich wesentliche Rolle und ist auch in den Abbildungen, wenn auch indirekt, erkennbar. Die kummulative Temperatur ist für 2021 fast ausschließlich positiv (wie auch für die meisten anderen Jahre der letzten Dekade). In der täglichen Temperatur sieht man außerdem eine Häufung von Hitzerekorden, die man in einem Klima öhne Erwärmung nicht erwarten würde.

Das kann man sich durch ein (etwas vereinfachtes) Beispiel gut vergegenwärtigen: Die Wahrscheinlichkeit, dass ein Tag in 2021 einen neuen Rekord aufstellt hängt in einem Klima ohne Änderungen nur von der Länge der Messreihe ab. Nehmen wir kurz an 2021 wäre das erste Jahr in dem wir messen, die Wahrscheinlichkeit, dass ein Tag einen neuen Rekord aufstellt ist also 100% (ziemlich trivial). Wenn wir hingegen auch Messwerte von 2020 berücksichtigen, kann 2021 darüber oder darunter liegen, hat also eine 50% Change einen neuen Rekord aufzustellen. In unserem Fall haben wir bereits Messungen von 1950-2020, das sind 71 Jahre (Anfangs- und Endjahr inkludiert). Das heißt ein Tag in 2021 hat eine Change von 1/71 oder ca. 1,4% auf einen neuen Rekord. 2021 hatte 365 Tage mal 1,4% ergibt das ca. 5 Tage. In einem Klima ohne Erwärmung erwarten wir also 5 Tage mit einem neuen Hitzerokord (übrigends auch 5 Tage mit einem neuen Kälterekord).

Was wir in der Zeitreihe der Tagesmitteltemperatur von 2021 sehen sind aber 11 Tage mit einem neuen Hitzerekord (und ein Tag mit einem neuen Kälterekord, der allerdings nicht markiert ist). Ähnlich verhält es sich wiederum für die anderen Jahre der letzten Dekade.


Der größere Kontext
---

TODO
