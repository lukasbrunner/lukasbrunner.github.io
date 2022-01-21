---
title: "Temperatur Updates von einem Twitter Bot"
excerpt: "<img src='/images/twitter_bot.png' width='40%'>"
collection: misc
permalink: /misc/twitter_bot_dt
---

This post is only available in German. You can visit the bot on <a href="https://twitter.com/tas_to_date" target="_blank">Twitter</a> or have a look at the code on <a href="https://github.com/lukasbrunner/tas_to_date" target="_blank">GitHub</a>.

Die Idee für dieses Projekt geht auf eine Diskussion um Ostern 2021 zurück. Wir konnten uns damals nicht einigen ob das Jahr in Österreich bisher besonders warm oder besonders kalt gewesen war. Um diese Frage zu beantworten schaue ich mir hier die Temperatur gemittelt über Österrreich und gemittelt vom 1. Jänner bis zu einem bestimmten Tag im Jahr an (also zum Beispiel on 1. Jänner bis Ostern). Ich vergleiche sie dann mit der Temperatur im selben Zeitraum in früheren Jahren.

Inzwischen schreiben wir 2022 und es ist möglich sich den Verlauf über ganz 2021 anzuschauen. In der daraus resultierenden Zeitreihe ist die Temperature an jedem Tag der zeitliche Mittelwert der Temperatur von 1. Jänner bis zu diesem Tag. Ich nenne das die **kumulative Mitteltemperatur**, angelehnt an das Konzept der kumulativen Summe (<a href="https://de.wikipedia.org/wiki/CUSUM" target="_blank">CUMSUM</a>).

Die kumulative Mitteltemperatur am 1. Jänner selbst ist also gleich der Tagestemperatur am 1. Jänner, während die kumulative Mitteltemperature am 31. Dezember gleich der Jährlichen Mitteltemperatur ist. Der Vergleich mit vergangenen Jahren ermöglicht eine aussage darüber ob das Jahr im Durchschnitt bisher unüblich warm oder unüblich kalt war. Ich verwende dafür zwei Metriken: die Abbweichung vom langjährigen Mittel (1950-2021) und den Rang.

Wie man in der Abbildung unten sehen kann war die kumulative Mitteltemperatur am 4. April 2021, dem Ostersonntag, um 1.1°C höher als im langjährigen Mittel und die 19. wärmste in den letzten 72 Jahren. Die richtige Antwort für die eingangs erwähnte Diskussion wäre also, dass das Jahr 2021 bis Ostern wärmer war als die meisten der 71 Jahre davor aber nicht zu den extremsten Jahren gehörte.

<img src="/images/bot/tas_cummean_austria_2021_094.jpg" width="80%" height="80%">

Einige andere Sache, die bei der Abbildung oben sofort ins Aufg fällt ist, dass der graue Bereich mit fortschreitendem Jahr immer enger wird. Das ist eine konsequenz aus dem Mittelwert: am Anfang des Jahres wird nur über wenige Tage gemittelt, das heißt jeder zusätzliche Tag hat vergleichsweiße viel Einfluß, während am Ende des Jahres über 300+ Tage gemittelt wird, ein einzelner Tag daher kaum mehr einen Einfluss hat. Das kann man auch bereits für 2021 an der roten Linie erkennen: anfangs schwankt sie recht starkt aber ab circa März scheint sie sich einzupendeln und bleibt relativ stabil. Was man aus der Abbildung (Werte ganz rechts) ebenfalls erkennt ist, dass die Jährliche Mitteltemperatur in Österreich scheinbar etwa 6°C ist mit einer Schwankungsbreite von etwa +/- 2°C.

In diesem Kontext ist es natürlich interessan die kumulative Mitteltemperatur mit der täglichen Temperature zu vergleichen. Da wir diese jeden Tag subjektiv erleben beeinflusst sie unsere Wahrnehmung auch stärker als eine über Monate gemittelte Temperatur. Die Abbildung unten ist ähnlich zur letzten Abbildung, zeigt aber für jeden Tag einfach die Temperatur an diesem Tag.

<img src="/images/bot/tas_daily_austria_2021_094.jpg" width="80%" height="80%">

Was man sofort erkennt ist die deutlich größere Schwankung, die -anders als für die kumulative Mitteltemperatur- übers Jahr nicht abnimmt. Bis Ostern hatte 2021 tatsächlich auch bereits 6 Tage, die einen neuen Temperaturerekord in Österreich aufgestellt hatten (in der Abbildung unden markiert). Gleichzeitig hab es aber auch drei Perioden mit Temperaturen deutlich unter dem langjährigen Mittel, eine kurz vor Ostern während der sogar ein neuer Kälterekord aufgestellt wurde. Es ist also vielleicht auch nicht verwunderlich wenn der einer oder die andere in unserer Diskussion zu Ostern den Eindruck hatte als wäre 2021 bisher sehr kalt gewesen.

<img src="/images/bot/tas_both_austria_2021_365_stepsize-auto_delay-40_size-1000.gif" width="80%" height="80%">


To the <a href="https://twitter.com/tas_to_date" target="_blank">Bot on Twitter</a>.


It all started with a family discussion over Easter 2021 where my parents could not decide if 2021 has been really cold or really warm in Austria so far. So I did the only reasonable thing and started making plots. I compared mean temperature from the beginning of the year until Easter to the same period in past years using data from ERA5. As seen in the figure below Austrian mean temperatures in 2021 until beginning of April where below the mean of the last 11 years but still 1.5°C above the 1950-1999 baseline.

<img src="/images/temperature_todate_2021-04-04.png" width="80%" height="80%">

Then I generalised it to any end date (i.e., mean temperature from January 1st to XX) in what I started calling year-to-date temperature. I also added to option to calculate the metric for different regions. As a test bed I used the regions defined for the latest sixth IPCC assessment report (AR6). The animation below shows the example of global temperature until end of April.

<img src="/images/temperature_todate_2021-04-28.gif" width="80%" height="80%">

Next I started to automate things using the very convenient <a href="https://era5cli.readthedocs.io/" target="_blank">era5cli</a> and <a href="https://en.wikipedia.org/wiki/Cron" target="_blank">cron</a> to download ERA5 (using the <a href="https://confluence.ecmwf.int/display/CKB/How+to+download+ERA5" target="_blank">ERA5 API</a>). My experience from this is that ERA5 is about 2 weeks behind real time which I find pretty impressive for a global reanalysis. Here is an example to download all available days from the current month and year in hourly resolution and then resample them to daily using <a href="https://code.mpimet.mpg.de/pürojects/cdo" target="_blank">cdo</a>:


```bash
<!-- year=$(date +%Y)  # current year -->
<!-- month=$(date +%m)  # current month -->
<!-- era5cli "hourly" --variables "2m_temperature" --startyear $year --months $month --outputprefix era5-${month}) -->
<!-- # define fn & fn_new -->
<!-- cdo daymean $fn $fn_new -->
<!-- ``` -->

<!-- I use a similar approach to update the plots in a directory. I've recently updated the layout of the plots a bit but haven't managed to clean to code up to a point where I think it is clean and documented enough to publish it. But one of these days... Here is mean temperature in the first half of 2021 for the Mediterranean in the new layout: -->

<!-- <img src="/images/temperature_todate_2021-06-30.png" width="80%" height="80%"> -->


<!-- Finally, I started to play around with the <a href="https://developer.twitter.com/en/docs/twitter-api" target="_blank">Twitter API</a> and applied for a developer account. I used the Python <a href="https://www.tweepy.org/" target="_blank">Tweepy</a> package, which makes automated tweeting pretty easy. At the core it is really only a couple of lines: -->

<!-- ```python -->
<!-- import tweepy -->

<!-- # ... -->

<!-- def tweet(fn, text): -->
<!--     auth = tweepy.OAuthHandler(consumer_key, consumer_key_secret) -->
<!--     auth.set_access_token(access_token, access_token_secret) -->
<!--     api = tweepy.API(auth) -->
<!--     media = api.media_upload(fn) -->
<!--     api.update_status(status=text, media_ids=[media.media_id]) -->
<!-- ``` -->

<!-- <img src="/images/twitter_bot.png" width="80%" height="80%"> -->
