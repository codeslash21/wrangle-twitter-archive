# Wrangle Twitter Archive

## Table of contents:

- <a href="#intro">Introduction </a>
- <a href="#data">Dataset </a>
- <a href="#software">What software do I need? </a>
- <a href="#steps">Project Steps </a>

<div id="intro>
         
</div>
## Introduction:

In this project we wrangle the tweet archive of Twitter user @dog_rates, also known as <a href="https://en.wikipedia.org/wiki/WeRateDogs"> WeRateDogs</a>. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. They rate the dogs almost
always with a denominator of 10. But numerators?? Most of them are greater than 10. But WHY??? WeRateDogs believes every dog is beautiful and almost all dogs deserve 10 and sometimes more than that. WeRateDogs has over 8 million followers and has received international media coverage. Our goal is to wrangle WeRateDogs Twitter data to create interesting and trustworthy analyses and visualizations.

<div id="data">
  
## Dataset:

The dataset consists of three parts. 
- **Enhanced twitter archive:** 
The WeRateDogs Twitter archive contains basic tweet data for all 5000+ of their tweets, but not everything. One column the archive does contain though: each tweet's text, which I used to extract rating, dog name, and dog "stage" (i.e. doggo, floofer, pupper, and puppo) to make this Twitter archive "enhanced." Of the 5000+ tweets, I have filtered for tweets with ratings only (there are 2356). This data is stored in `twitter_archive_enhanced.csv` file.

- **Additional Data via the Twitter API:**
Back to the basic-ness of Twitter archives: retweet count and favorite count are two of the notable column omissions. Fortunately, this additional data can be gathered by anyone from Twitter's API. Well, "anyone" who has access to data for the 3000 most recent tweets, at least. We have the WeRateDogs Twitter archive and specifically the tweet IDs within it, we can gather this data for all 5000+. We're going to query Twitter's API to gather this valuable data. Finally we store these data in `tweet_json.txt` file.

- **Image Predictions File:**
One more cool thing: I ran every image in the WeRateDogs Twitter archive through a neural network that can classify breeds of dogs*. The results: a table full of image predictions (the top three only) alongside each tweet ID, image URL, and the image number that corresponded to the most confident prediction (numbered 1 to 4 since tweets can have up to four images). We store this prediction data in `image_predictions.tsv` file.

<div id="software">
  
## What Software Do I Need?
One can do this project in jupyter notebook using python 3.x But one has to install the following python packages to wrangle dataset and query twitter api.

> - pandas
> - NumPy
> - requests
> - tweepy
> - json
> - sqlalchemy
  
<div id="steps">
  
## Project Steps:
Basically data wrangling process consissts of three steps. These are follows -

- **Gather Data:** Gather dataset for wrangling.
- **Assess Data:** Note the issues regarding quality and tidiness of the dataset.
- **Clean Data:** Here we fixing issues those are documented during data assessment process to make dataset ready for analysis.

Its recomended that after data wrangling process, clean data should be stored for future analysis purpose. Here we store the clean data in a flat file `twitter_archive_master.csv` and a sqlite database `twitter.db`.
