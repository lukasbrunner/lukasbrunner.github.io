---
title: "Kumulative Mitteltemperatur in Österreich"
excerpt: "<img src='/images/bot/tas_cummean_austria_2021_365_stepsize-auto_delay-40_size-1000.gif' width='60%'>"
collection: misc
permalink: /misc/twitter_bot_dt
---

<em>This post is only available in German but you can have a look at the English code documentation on <a href="https://github.com/lukasbrunner/tas_to_date" target="_blank">GitHub</a>.</em>

<em>Dieser Artikel ist eine allgemein verstänliche Erklärung der Hintergründe meines <a href="https://twitter.com/tas_to_date" target="_blank">Twitter Bots</a>. Detailierte Informationen sowie der Quellcode sind auf <a href="https://github.com/lukasbrunner/tas_to_date" target="_blank">GitHub</a> verfügbar (in Englisch).</em>
<br /><br />

Die Idee für dieses Projekt geht auf eine Diskussion um Ostern 2021 zurück. Wir konnten uns damals nicht einigen ob das Jahr in Österreich bisher besonders warm oder besonders kalt gewesen war. Um diese Frage zu beantworten schaue ich mir hier die Temperatur gemittelt über Österrreich und gemittelt vom 1. Jänner bis zu einem bestimmten Tag im Jahr an (also zum Beispiel on 1. Jänner bis Ostern). Ich vergleiche sie dann mit der Temperatur im selben Zeitraum in früheren Jahren.

Inzwischen schreiben wir 2022 und es ist möglich sich den Verlauf über ganz 2021 anzuschauen. In der daraus resultierenden Zeitreihe ist die Temperature an jedem Tag der zeitliche Mittelwert der Temperatur von 1. Jänner bis zu diesem Tag. Ich nenne das die **kumulative Mitteltemperatur**, angelehnt an das Konzept der kumulativen Summe (<a href="https://de.wikipedia.org/wiki/CUSUM" target="_blank">CUMSUM</a>).

Die kumulative Mitteltemperatur am 1. Jänner selbst ist also gleich der Tagestemperatur am 1. Jänner, während die kumulative Mitteltemperature am 31. Dezember gleich der Jährlichen Mitteltemperatur ist. Der Vergleich mit vergangenen Jahren ermöglicht eine aussage darüber ob das Jahr im Durchschnitt bisher unüblich warm oder unüblich kalt war. Ich verwende dafür zwei Metriken: die Abbweichung vom langjährigen Mittel (1950-2021) und den Rang.

Wie man in der Abbildung unten sehen kann war die kumulative Mitteltemperatur am 4. April 2021, dem Ostersonntag, um 1.1°C höher als im langjährigen Mittel und die 19. wärmste in den letzten 72 Jahren. Die richtige Antwort für die eingangs erwähnte Diskussion wäre also, dass das Jahr 2021 bis Ostern wärmer war als die meisten der 71 Jahre davor aber nicht zu den extremsten Jahren gehörte.

<img src="/images/bot/tas_cummean_austria_2021_094.jpg" width="100%">

Einige andere Sache, die bei der Abbildung oben sofort ins Aufg fällt ist, dass der graue Bereich mit fortschreitendem Jahr immer enger wird. Das ist eine konsequenz aus dem Mittelwert: am Anfang des Jahres wird nur über wenige Tage gemittelt, das heißt jeder zusätzliche Tag hat vergleichsweiße viel Einfluß, während am Ende des Jahres über 300+ Tage gemittelt wird, ein einzelner Tag daher kaum mehr einen Einfluss hat. Das kann man auch an der roten Linie von 2021 erkennen: anfangs schwankt sie recht starkt aber ab circa März scheint sie sich einzupendeln und bleibt relativ stabil.

In diesem Kontext ist es natürlich auch interessant die kumulative Mitteltemperatur mit der täglichen Temperature zu vergleichen. Da wir diese jeden Tag subjektiv erleben beeinflusst sie unsere Wahrnehmung vermutlich stärker als eine über Monate gemittelte Temperatur. Die Abbildung unten ist ähnlich zur letzten Abbildung, zeigt aber für jeden Tag einfach die Temperatur an diesem Tag.

<img src="/images/bot/tas_daily_austria_2021_094.jpg" width="100%">

Was man sofort erkennt ist die deutlich größere Schwankung, die  &ndash;anders als für die kumulative Mitteltemperatur &ndash; übers Jahr nicht abnimmt. Bis Ostern hatte 2021 tatsächlich auch bereits 6 Tage, die einen neuen Hitzerekord in Österreich aufgestellt hatten. Gleichzeitig hab es aber auch drei Perioden mit Temperaturen deutlich unter dem langjährigen Mittel, eine kurz vor Ostern während der sogar ein neuer Kälterekord aufgestellt wurde. Es ist also auch nicht wirklich verwunderlich wenn der einer oder die andere in unserer Diskussion zu Ostern den Eindruck hatte als wäre 2021 bisher eher kalt gewesen.

Die Animation unten zeigt die Entwicklng der Tagesmitteltemperatur und kumulativen Mitteltemperatur in Österreich während ganz 2021. Man sieht wie die tägliche Temperatur die kumulativen Temperatur anfangs stark beeinflusst, während der Einfluss gegen Ende des Jahres abnimmt aber. Aber gerade längere sehr warme Perioden wie zum Beispiel Mitte Juni können die kumulative Temperature weiterhin beeinflussen (in diesem Fall erhöhen). Im Jährlichen Mittel landet 2021 mit 0,8°C über dem langjährigen Mittwelwert (1950-2021) auf Rang 18/72.

<img src="/images/bot/tas_both_austria_2021_365_stepsize-auto_delay-40_size-1000.gif" width="100%">

<!-- https://www.zamg.ac.at/cms/de/klima/klima-aktuell/klimamonitoring/?param=t&period=period-y-2021&ref=3 -->

Der Einlfuss des Klimawandels
---

Ich habe mich in dieser Betrachtung der Temperatur in Österreich nicht explizit mit dem Klimawandel auseinandergesetzt. Aber implizit spielt er natürlich eine wesentliche Rolle und ist auch in den Abbildungen bereits für ein Jahr zumindest erahnbar. In der täglichen Temperatur sieht man nämlich eine Häufung von Hitzerekorden, die man in einem Klima ohne Erwärmung nicht erwarten würde.

Das kann man sich durch ein einfaches Beispiel gut vergegenwärtigen: Die Wahrscheinlichkeit, dass ein Tag in 2021 einen neuen Rekord aufstellt hängt in einem Klima ohne Änderungen nur von der Länge der Messreihe ab. Nehmen wir kurz an 2021 wäre das erste Jahr in dem wir messen, die Wahrscheinlichkeit, dass ein Tag einen neuen Rekord aufstellt ist also 100%. Wenn wir hingegen auch Messwerte von 2020 berücksichtigen, kann 2021 darüber oder darunter liegen, hat also eine 50% Change einen neuen Rekord aufzustellen. Im tatsächlich gezeigen Fall haben wir bereits Messungen von 1950-2020, das sind 71 Jahre (Anfangs- und Endjahr inkludiert). Das heißt ein Tag in 2021 hat eine Change von 1/71 oder ca. 1,4% auf einen neuen Rekord. 2021 hatte 365 Tage mal 1,4% ergibt das ca. 5 Tage. In einem Klima ohne Erwärmung erwarten wir also 5 Tage mit einem neuen Hitzerokord (übrigends auch 5 Tage mit einem neuen Kälterekord).

Was wir in der Zeitreihe der Tagesmitteltemperatur von 2021 sehen sind aber 11 Tage mit einem neuen Hitzerekord (und ein Tag mit einem neuen Kälterekord, der allerdings nicht markiert ist).

<img src="/images/bot/tas_daily_austria_2021_365.jpg" width="100%">


Österreich im größeren Kontext
---

Äquivalent zu Österreich können wir uns auch andere Regionen und deren Temperaturverlauf anschauen. Als Beispiel verwende ich hier 3 weitere Regionen: Zentraleuropa, Europa und Global. Diese 3 Regionen stellen gewissermaßen ein herauszoomen zu immer größeren Skalen dar.

<img src="/images/bot/tas_daily_wce-land_2021_365.jpg" width="100%">
<img src="/images/bot/tas_daily_europe_2021_365.jpg" width="100%">
<img src="/images/bot/tas_daily_global_2021_365.jpg" width="100%">

TODO


Daten, Quellcode und Twitter Bot
---

TODO
