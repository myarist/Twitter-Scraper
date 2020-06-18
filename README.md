# Twitter Scraper for Covid-19

Here, I use two methods for doing scrape to get the Twitter data about Covid-19.

## GetOldTweets3

In this module, I don't use Twitter API.
On this module, I use some filter, such as:

```
... TweetCriteria().setQuerySearch(kata_kunci)\
                   .setSince(tanggal_mulai)\
                   .setUntil(tanggal_akhir)\
                   .setNear(di_daerah_rad)\
                   .setMaxTweets(batas_mencari)
```

Filters | Function
:---: | :---
kata_kunci | Look for Tweets that contain the word
tanggal_mulai | Look for Tweets starting from the given date
tanggal_akhir | Look for Tweets until the given date
di_daerah_rad | Look for Tweets that are in the area around it
batas_mencari | Look for Tweets of a given number of limits

Then, from this module, several variables are taken including:

```
text_tweets = [[tw.username,
                tw.text,
                tw.date,
                tw.retweets,
                tw.favorites,
                tw.mentions,
                tw.hashtags] for tw in tweet]
```

Variables | Contents
:---: | :---
username | The name of the person who created the Tweet
text | Full text of Tweets
date | The date the Tweet was sent
retweets | Number of people who retweeted
favorites | The number of people who make it a Favorite
mentions | Number of people doing Mention
hastags | List of hashtags that are in Tweets

