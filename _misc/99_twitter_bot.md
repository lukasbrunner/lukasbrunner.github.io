---
title: "Writing a Twitter Bot to post temperature updates"
excerpt: "<img src='/images/twitter_bot.png' width='60%'>"
collection: misc
permalink: /misc/twitter_bot
---
<!-- Nice Twitter integration does not seem to be possible: -->
<!-- - https://stackoverflow.com/questions/49085236/cant-render-twitter-stream-in-github-pages -->
<!-- I've also tried this: -->
<!-- - https://github.com/rob-murray/jekyll-twitter-plugin -->

To the <a href="https://twitter.com/tas_to_date" target="_blank">Bot on Twitter</a>.


It all started with a family discussion over Easter 2021 where my parents could not decide if 2021 has been really cold or really warm in Austria so far. So I did the only reasonable thing and started making plots. I compared mean temperature from the beginning of the year until Easter to the same period in past years using data from ERA5. As seen in the figure below Austrian mean temperatures in 2021 until beginning of April where below the mean of the last 11 years but still 1.5°C above the 1950-1999 baseline.

<img src="/images/temperature_todate_2021-04-04.png" width="80%" height="80%">

Then I generalised it to any end date (i.e., mean temperature from January 1st to XX) in what I started calling year-to-date temperature. I also added to option to calculate the metric for different regions. As a test bed I used the regions defined for the latest sixth IPCC assessment report (AR6). The animation below shows the example of global temperature until end of April.

<img src="/images/temperature_todate_2021-04-28.gif" width="80%" height="80%">

Next I started to automate things using the very convenient <a href="https://era5cli.readthedocs.io/" target="_blank">era5cli</a> and <a href="https://en.wikipedia.org/wiki/Cron" target="_blank">cron</a> to download ERA5 (using the <a href="https://confluence.ecmwf.int/display/CKB/How+to+download+ERA5" target="_blank">ERA5 API</a>). My experience from this is that ERA5 is about 2 weeks behind real time which I find pretty impressive for a global reanalysis. Here is an example to download all available days from the current month and year in hourly resolution and then resample them to daily using <a href="https://code.mpimet.mpg.de/projects/cdo" target="_blank">cdo</a>:


```bash
year=$(date +%Y)  # current year
month=$(date +%m)  # current month
era5cli "hourly" --variables "2m_temperature" --startyear $year --months $month --outputprefix era5-${month})
# define fn & fn_new
cdo daymean $fn $fn_new
```

I use a similar approach to update the plots in a directory. I've recently updated the layout of the plots a bit but haven't managed to clean to code up to a point where I think it is clean and documented enough to publish it. But one of these days... Here is mean temperature in the first half of 2021 for the Mediterranean in the new layout:

<img src="/images/temperature_todate_2021-06-30.png" width="80%" height="80%">


Finally, I started to play around with the <a href="https://developer.twitter.com/en/docs/twitter-api" target="_blank">Twitter API</a> and applied for a developer account. I used the Python <a href="https://www.tweepy.org/" target="_blank">Tweepy</a> package, which makes automated tweeting pretty easy. At the core it is really only a couple of lines:

```python
import tweepy

# ...

def tweet(fn, text):
    auth = tweepy.OAuthHandler(consumer_key, consumer_key_secret)
    auth.set_access_token(access_token, access_token_secret)
    api = tweepy.API(auth)
    media = api.media_upload(fn)
    api.update_status(status=text, media_ids=[media.media_id])
```

<img src="/images/twitter_bot.png" width="80%" height="80%">
