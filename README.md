# Predicting Hit Songs Utilizing Spotify

## Introduction

Major music record labels are a powerful asset for an upcoming artist's success. The majority of artists one would see on the Billboard Top 100 charts are signed by one of the three major record labels: Universal Music Group, Sony Music Entertainment, and Warner Music Group. The average listener is aware of the song and the artist, however, the production of the music goes way deeper. Record labels work behind the scenes to produce, market, and optimize songs in order to generate profit from their content.

There are many factors that go into creating a hit song. The right artist has to be matched with a song, the recording of the song must be spectacular, the production team must be able to promote the song effectively, and the release date would also play an important role.

For this project, I will create a machine learning model that would be capable of classifying whether a song will land in the Billboard Top 100 or not.

## Creation of the Dataset

The dataset was built from a sample of over 10,000 songs through the Spotify API. The collection of hits from 2010 - 2020 were taken from playlists that users have created. Thank you to the following Spotify users for creating the End of Year Hot-100 Billboard Playlists:  martinh0205 (2010), Courtney Micky Ericks (2011), 11165570549 (2012), gisi0722 (2013), cegomez12 (2014, 2015), wickeddreamer96 (2016, 2017), whe1998 (2018), 21ksdt3ca2433ykekswnkdmi (2019), and Oscar Zheng (2020).

The songs were collected from the past decade since song trends have changed over time and I inferred that analyzing recent hit songs would lead to more accurate predictions. The audio features of each song were extracted and were utilized as the independent variables for this analysis.

|Feature|Type|Dataset|Description|
|---|---|---|---|
|danceability|float|songs_clean|Measure of danceability of a song. Combination of musical elements: tempo, rhythm, beat strength|
|energy|float|songs_clean|Measure of intensity and activity|
|key|int|songs_clean|State Measure of pitch in a song|
|loudness|float|songs_clean|Overall loudness (dB)|
|mode|int|songs_clean|Measure of tonality|
|speechiness|float|songs_clean|Measure of spoken words|
|instrumentalness|float|songs_clean|Measure of vocal content|
|liveness|float|songs_clean|Presence of an audience in the recording|
|valence|float|songs_clean|Measure of positiveness (happy/cheerful vs. sad/angry)|
|tempo|float|songs_clean|Mean beats per min (BPM)|
|duration_ms|int|songs_clean|Duration of the song (ms)|
|time_signature|int|songs_clean|Measure of beats per measure|
|release_day|int|songs_clean|Day the song was released|
|release_month|int|songs_clean|Month the song was released|
|hit|int|songs_clean|Whether the song landed in the Billboard Top 100|

## Summary

The selection of songs were critical, I wanted to select a sample size that included songs from various genres. I utilized the Spotify API to scrape audio data from Spotify curated playlists. My data consisted of over 14,000 songs.

Data cleaning was very minimal since I scraped the song data from Spotify. The biggest concern were duplicate songs from the playlists I scraped. Ultimately, after the cleaning process, I had a dataset of about 12,000 songs. Approximately 10,800 songs were non-hits and 975 songs were hits. Less than 9% of songs were labelled as hits which leads to a major imbalance of classes.

In order to address the problem of class imbalance, I utilized the synthetic minority oversampling tehcnique method (SMOTE). This allowed me to balance the classes to a near 50/50 split. Once this was complete, I was ready to train my models. A random seed was set so that I was able to compare my models.

## Evaluations
|Model|Accuracy|Precision|Recall|F1 Score|
|---|---|---|---|---|
|Logistic Regression|.76|.728|.83|.78|
|KNN|.831|.753|.986|.854|
|Random Forest|.837|.775|.95|.853|
|Voting Tree|.894|.864|.935|.90|
|SVM|.853|.80|.948|.866|
|Neural Network|.856|.822|.916|.867|

Accuracy and the F1 score were my success metrics for this project. Accuracy shows the ratio of correctly predicted observations to the total observations. The F1 score is the weighted average of precision and recall. This score is vital since misclassifying a hit song and a nonhit song have a similar cost.

Depending on the amount of risk a label would be willing to take, a label can choose a model that has high accuracy in hopes that they will discover more hit songs. On the other hand, if the label is willing to reduce risk, they would choose a model that has a high F1 score to minimize the number of false positives and false negatives.

The voting tree classifier model performed the best with an accuracy of .894 and a F1 score of .90.

## Conclusion & Recommendations

The goal of this project was to create a machine learning model that is capable of predicting a hit independent of the artist and production metrics. My results show that it is within reason to create a ML model that can predict a hit song with reasonable accuracy and precision. I was able to achieve that with a voting tree model with an accuracy and F1 score of approximately 90%.

It is important to remember that Spotify houses this data and the features were built off of Spotify's metrics. An important metric that was proprietary to Spotify was the listen count. This metric would be vital to create a regression model that can predict the listen rate of a song.

In this study, I defined a hit song as a song that landed in the Billboard Top 100 Chart. However, there are many ways to define a hit, one can utilize the popularity score or other metrics to define a hit song. In addition, there are a finite number of hit songs if one were to define a hit song as a song that landed in the Billboard Top 100. By adding more songs to train the model, the imbalance of classes will only get greater. While SMOTE can be effective in addressing severely unbalanced classes, it blindly generates the minority population without regard to the majority class. This can lead to a greater risk of class mixture.

Spotify is quietly [disrupting the music industry](https://www.nytimes.com/2018/09/06/business/media/spotify-music-industry-record-labels.html). While the Chief Executive Officer, Dan Ek, made it clear that Spotify does not plan on owning the license to the content, they are enabling independent artists to maximize profits by partnering with a streaming service with Spotify. My attempt at creating a predictive model serves as an example of how Spotify can automate the search for the next "hit" song. One can imagine that this may lead to the downfall of traditional music record labels and the rise of streaming services such as Spotify, Apple Music, and Google Play.
