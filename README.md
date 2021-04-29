# Predicting Hit Songs

## Introduction

Major music record labels are a powerful asset for an upcoming artist's success. The majority of artists one would see on the Billboard Top 100 charts are signed by one of the three major record labels: Universal Music Group, Sony Music Entertainment, and Warner Music Group. The average listener is aware of the song and the artist, however, the production of the music goes way deeper. Record labels work behind the scenes to produce, market, and optimize songs in order to generate profit from their content.

There are many factors that go into creating a hit song. The right artist has to be matched with a song, the recording of the song must be spectacular, the production team must be able to promote the song effectively, and the release date would also play an important role.

For this project, I will create a machine learning model that would be capable of classifying whether a song will land in the Billboard Top 100 or not.

## Creation of the Dataset

The dataset was built from a sample of over 10,000 songs through the Spotify API. The collection of hits from 2010 - 2020 were taken from playlists that users have created. Thank you to the following Spotify users for creating the End of Year Hot-100 Billboard Playlists: Rudy Evan (2000 - 2009), martinh0205 (2010), Courtney Micky Ericks (2011), 11165570549 (2012), gisi0722 (2013), cegomez12 (2014, 2015), wickeddreamer96 (2016, 2017), whe1998 (2018), 21ksdt3ca2433ykekswnkdmi (2019), and Oscar Zheng (2020).

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

## EDA

## Modelling


## Evaluations

## Conclusion & Recommendations
