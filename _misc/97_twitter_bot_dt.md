---
title: "Kumulative Mitteltemperatur in Österreich"
excerpt: "<img src='/images/bot/tas_cummean_austria_2021_365_stepsize-auto_delay-40_size-1000.gif' width='60%'>"
collection: misc
permalink: /misc/cummean
---

<em>This post is only available in German but you can have a look at the English code documentation on <a href="https://github.com/lukasbrunner/tas_to_date" target="_blank">GitHub</a>.</em>

<em>Dieser Artikel ist eine allgemein verständliche Erklärung der Hintergründe meines <a href="https://twitter.com/tas_to_date" target="_blank">Twitter Bots</a>. Detailierte Informationen sowie der Quellcode sind auf <a href="https://github.com/lukasbrunner/tas_to_date" target="_blank">GitHub</a> verfügbar (in Englisch).</em>
<br /><br />

Die Idee für dieses Projekt geht auf eine Diskussion um Ostern 2021 zurück. Wir konnten uns damals nicht einigen ob das Jahr in Österreich bisher besonders warm oder besonders kalt gewesen war. Um diese Frage zu beantworten schaue ich mir hier die Temperatur gemittelt über Österreich und gemittelt vom 1. Jänner bis zu einem bestimmten Tag im Jahr an (also zum Beispiel on 1. Jänner bis Ostern). Ich vergleiche sie dann mit der Temperatur im selben Zeitraum in früheren Jahren.

Inzwischen schreiben wir 2022 und es ist möglich sich den Verlauf über ganz 2021 anzuschauen. In der daraus resultierenden Zeitreihe ist die Temperature an jedem Tag der zeitliche Mittelwert der Temperatur von 1. Jänner bis zu diesem Tag. Ich nenne das die **kumulative Mitteltemperatur**, angelehnt an das Konzept der kumulativen Summe (<a href="https://de.wikipedia.org/wiki/CUSUM" target="_blank">CUMSUM</a>).

<img src="/images/bot/tas_cummean_austria_2021_094.jpg" width="100%">

Der Vergleich mit vergangenen Jahren ermöglicht eine aussage darüber ob das Jahr im Durchschnitt bisher unüblich warm oder unüblich kalt war. Ich verwende dafür zwei Metriken: die Abweichung vom langjährigen Mittel (1950-2021) und den Rang. Wie man in der Abbildung sehen kann war die kumulative Mitteltemperatur am 4. April 2021, dem Ostersonntag, um 1.1°C höher als im langjährigen Mittel und die 19. wärmste in den letzten 72 Jahren. Die richtige Antwort für die eingangs erwähnte Diskussion wäre also, dass das Jahr 2021 bis Ostern wärmer war als die meisten der 71 Jahre davor aber nicht zu den extremsten Jahren gehörte.

Eine andere Sache, die bei der Abbildung oben sofort ins Auge fällt ist, dass der graue Bereich mit fortschreitendem Jahr immer enger wird. Das ist eine konsequenz aus dem Mittelwert: am Anfang des Jahres wird nur über wenige Tage gemittelt, das heißt jeder zusätzliche Tag hat vergleichsweise viel Einfluß, während am Ende des Jahres über 300 oder mehr Tage gemittelt wird und ein einzelner zusätzlicher Tag daher kaum Einfluss hat. Das kann man auch an der roten Linie von 2021 erkennen: anfangs schwankt sie recht stark aber ab circa März scheint sie sich einzupendeln und bleibt relativ stabil.

In diesem Kontext ist es auch interessant die kumulative Mitteltemperatur mit der täglichen Temperatur zu vergleichen. Da wir diese jeden Tag subjektiv erleben beeinflusst sie unsere Wahrnehmung vermutlich stärker als eine über Monate gemittelte Temperatur. Die Abbildung unten ist ähnlich zur letzten Abbildung, zeigt aber für jeden Tag einfach die Temperatur an diesem Tag.

<img src="/images/bot/tas_daily_austria_2021_094.jpg" width="100%">

Was man sofort erkennt ist die deutlich größere Schwankung, die  &ndash;anders als für die kumulative Mitteltemperatur&ndash; übers Jahr nicht abnimmt. Bis Ostern hatte 2021 tatsächlich bereits 6 Tage, die einen neuen Hitzerekord in Österreich aufgestellt hatten. Gleichzeitig hab es aber auch drei Perioden mit Temperaturen deutlich unter dem langjährigen Mittel darunter auch der Ostersonntag, der auf eine ungewöhnlich warme Periode folgte. Es ist also auch nicht wirklich verwunderlich wenn der einer oder die andere in unserer Diskussion zu Ostern den Eindruck hatte als wäre 2021 bisher eher kalt gewesen.

Die Animation unten zeigt die Entwicklung der Tagesmitteltemperatur und kumulativen Mitteltemperatur in Österreich während dem ganzen Jahr 2021. Man sieht wie die tägliche Temperatur die kumulativen Temperatur anfangs stark beeinflusst, während der Einfluss gegen Ende des Jahres abnimmt aber. Im Jährlichen Mittel landet 2021 in Österreich mit 0,8°C über dem langjährigen Mittelwert (1950-2021) auf Rang 18/72.

<img src="/images/bot/tas_both_austria_2021_365_stepsize-auto_delay-40_size-1000.gif" width="100%">

<!-- https://www.zamg.ac.at/cms/de/klima/klima-aktuell/klimamonitoring/?param=t&period=period-y-2021&ref=3 -->

Der Einfluss des Klimawandels
---

Ich habe mich in dieser Betrachtung der Temperatur in Österreich nicht explizit mit dem Klimawandel auseinandergesetzt. Aber implizit spielt er natürlich eine wesentliche Rolle und ist auch in den Abbildungen bereits für ein einzelnes Jahr bereits erkennbar. In der täglichen Temperatur sieht man nämlich eine Häufung von Hitzerekorden, die man in einem Klima ohne Erwärmung nicht erwarten würde.

Das kann man sich durch ein einfaches Beispiel gut vergegenwärtigen: Die Wahrscheinlichkeit, dass ein Tag in 2021 einen neuen Rekord aufstellt hängt in einem Klima _ohne Änderungen_ nur von der Länge der Messreihe ab. Nehmen wir kurz an 2021 wäre das erste Jahr in dem wir messen, die Wahrscheinlichkeit, dass ein Tag einen neuen Rekord aufstellt ist also 100%. Wenn wir hingegen auch Messwerte von 2020 berücksichtigen, kann 2021 darüber oder darunter liegen, hat also eine 50% Chance einen neuen Rekord aufzustellen.

Im tatsächlich gezeigten Fall haben wir bereits Messungen von 1950-2020, das sind 71 Jahre (Anfangs- und Endjahr inkludiert). Das heißt ein Tag in 2021 hat eine Chance von 1/71 oder ca. 1,4% auf einen neuen Rekord. 2021 hatte 365 Tage mal 1,4% ergibt das ca. 5 Tage. Das heißt **in einem Klima ohne Erwärmung erwarten, wir 2021 5 Tage mit einem neuen Hitzerekord** (übrigends auch 5 Tage mit einem neuen Kälterekord).

Was wir in der Zeitreihe der Tagesmitteltemperatur von 2021 sehen sind aber 11 Tage mit einem neuen Hitzerekord (und nur ein Tag mit einem neuen Kälterekord, der allerdings nicht markiert ist). Für ein einzelnes Jahr könnte das natürlich Zufall sein, aber ähnliches lässt sich auch für die anderen Jahre der letzten Dekade zeigen.

<img src="/images/bot/tas_daily_austria_2021_365.jpg" width="100%">


Österreich im größeren Kontext
---

Äquivalent zu Österreich können wir uns auch andere Regionen und deren Temperaturverlauf anschauen. Als Beispiel verwende ich hier 2 weitere Regionen: Europa und Global. Diese beiden Regionen stellen gewissermaßen ein herauszoomen zu immer größeren Skalen dar. Was man auf den Abbildungen unten deutlich erkennt ist, dass die Schwankungen der Tagestemperatur mit zunehmender Regionsgröße abnehmen da man über immer mehr Fläche mittelt. Für Europa sind die Schwankungen der Temperatur aber durchaus noch mit Österreich vergleichbar, wenn auch glatter. Die Globale Temperatur weist vergleichsweise nur noch sehr schwache Schwankungen auf und ist über weite Teile von 2021 im Bereich der wärmsten 10%.

**Wichtig:** Die y-Achse ist in allen Abbildungen unterschiedlich. Im Vergleich zu Europa weist der Globale Fall kaum einen Jahresgang auf. Tatsächlich kann man sich fragen warum die globale Temperatur überhaupt einen Jahresgang hat, schließlich ist während des Sommers auf der Nordhalbkugel auf der Südhalbkugel Winter. Das liegt an der ungleichen verteilung der Landmassen, die im Norden mehr Fläche einnehmen und ihre Temperatur schneller ändern können als Ozeane.

<img src="/images/bot/tas_daily_europe_2021_365.jpg" width="100%">
<img src="/images/bot/tas_daily_global_2021_365.jpg" width="100%">

Die kumulative Mitteltemperatur zeigt, dass 2021 in Österreich über weite Strecken und insbesondere auch im Jährlichen Mittel relativ kühler war als Europa oder die Erde als gesamtes. Während das Jahr 2021 in Österreich letztlich Rang 18 belegte, ist es in Europa schon Rang 8 und Global überhaupt Rang 5.

<img src="/images/bot/tas_cummean_europe_2021_365.jpg" width="100%">
<img src="/images/bot/tas_cummean_global_2021_365.jpg" width="100%">


Daten und Quellcode
---

Alle Abbildungen basieren auf dem ERA5 Datensatz des Europäischen Zentrums für Mittelfristige Wettervorhersage (<a href="https://www.ecmwf.int/" target="_blank">ECMWF</a>). Die Daten sind für Forschungszwecke zum Beispiel vom Copernius Climate Data Store (CDS) frei verfügbar (<a href="https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels?tab=overview" target="_blank">Link</a>). Ich verwende täglich gemitteltelte bodennahe Lufttemperatur basierend auf stündlichen Daten mit einer Auflösung von 0,25° in geographischer Länge und Breite (ca. 25km am Äquator). Für den Download verwende ich die CDS API und das Tool <a href="https://era5cli.readthedocs.io" target="_blank">era5cli</a>, für das Berechnen der Täglichen Mittelwerte verwende ich das Tool <a href="https://code.mpimet.mpg.de/projects/cdo/embedded/index.html" target="_blank">cdo</a>:

```bash
era5cli "hourly" --variables "2m_temperature" --startyear "2021"  # -> $fn_hourly
cdo daymean $fn_hourly $fn_daily
```

Der Quellcode für die Datenprozessierung und das Erstellen der Abbildungen ist auf GitHub verfügbar: <a href="https://github.com/lukasbrunner/tas_to_date" target="_blank">link</a>. Die Jahre 1950-2021 sind für ausgewählte Regionen vorprozessiert, sodass Plot Routinen auch auf Heimrechnern ausführbar sein sollten. Voraussetzung ist eine aktuelle Version von Python (ich verwende 3.9) sowie einige spezialisierte Pakete, die aber mit etwas vorwissen einfach zu installieren sein sollten (zum Beispiel mit <a href="https://docs.conda.io/en/latest/miniconda.html#" target="_blank">conda</a>).

Mein <a href="https://twitter.com/tas_to_date" target="_blank">Twitter Bot</a>, der ebenfalls auf dem verlinkten Code baisert braucht zusätzlich aktuelle Temperatur Daten. Diese basieren auf ERA5T, der _near-real-time_ Variante von ERA5. Für das automatisierte Posten auf Twitter verwende ich <a href="https://www.linuxwiki.de/cron" target="_blank">cron</a> und die <a href="https://developer.twitter.com/en/docs/twitter-api" target="_blank">Twitter API</a>.
