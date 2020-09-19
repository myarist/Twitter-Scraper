# Twitter Scraper

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
favorites | Number of people who make it as favorite
mentions | List of mentions added
hastags | List of hashtags that are in Tweets

The following is an overview of the data obtained

![getold](https://github.com/MyArist/Twitter-Scraper-for-Covid-19/blob/master/README/get.png)

For more documentation, visit [GetOldTweets3](https://pypi.org/project/GetOldTweets3/)

## Twint

The other module, that do not use API.
On this module, I use some filter, such as:

```
c.Search = searchterm
c.Since = since
c.Until = until
c.Limit = 100
c.Lang = "id"
```

Filters | Function
:---: | :---
search | Look for Tweets that contain the word
since | Look for Tweets starting from the given date
until | Look for Tweets until the given date
limit | Look for Tweets of a given number of limits
lang | Lok for Tweets that use the language

This module give 34 total variables including:
- id
- username
- created date
- place
- text
- mentions
- urls
- photos
- (...)

![Twint](https://github.com/MyArist/Twitter-Scraper-for-Covid-19/blob/master/README/twint.png)

For more documentation, visit [Twint](https://github.com/twintproject/twint)

## Tweepy

In this module, I use Twitter API.
On this module, I use some filter, such as:

```
tweets = tw.Cursor(api.search, 
                   q                = new_search,
                   result_type      = "mixed",
                   lang             = "id",
                   count            = 100,
                   include_entities = True,
                   since_id         = "2020-01-01").items(2000)
```

Filters | Function
:---: | :---
q | Look for Tweets that contain the word
result_type | Consisting of Recent, Popular, and Mixed
lang | The language used
count | Number of Tweets per page
include_entities | Retrieves other optional attributes
since_id | Look for Tweets starting from the given date

Then, from this module, several variables are taken including:

```
users_locs = [[tweet.created_at,
               tweet.author.screen_name,
               tweet.author.name,
               tweet.text,
               tweet.retweet_count,
               tweet.favorite_count,
               tweet.user.location] for tweet in tweets]
```

Variables | Contents
:---: | :---
created_at | The date the Tweet was sent
author.screen_name | Unique name for the user
author.name | The name that appears
text | Full text of Tweets
retweet_count | Number of people who retweeted
favorite_count | Number of people who make it as favorite
user.location | Location when sending a Tweet

The following is an overview of the data obtained

![twee](https://github.com/MyArist/Twitter-Scraper-for-Covid-19/blob/master/README/twee.png)

For more documentation, visit [Tweepy](https://docs.tweepy.org/en/latest/api.html)
