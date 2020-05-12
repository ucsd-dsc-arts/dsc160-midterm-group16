# Project Title

DSC160 Data Science and the Arts - Midterm Project Repository - Spring 2020

Project Team Members: 
- Leon Kuo, lkuo@ucsd.edu
- Will Bates, wbates@ucsd.edu
- Saveree Joshipura, sjoshipu@ucsd.edu
- Nicole Lee, nml015@ucsd.edu
- Brandon Tsui, bhtsui@ucsd.edu

## Abstract

It is culturally understood that throughout the years, music by The Beatles transitioned from classic popular music to experimental music. We aim to quantify this transition. The goal of our project is to answer the following question: what features and/or trends defined eras of Beatles music, and how can we visually display that? Performing analysis on their music is fascinating for many reasons, especially quantifying their transition from popular music to experimental music and seeing the defining features and trends of each era. We scraped audio from https://archive.org/details/thebeatlesatozsongsstereoremastered and extracted features such as frequency, tempo, lyrics, and structure of each song. The labels came from a Wikipedia list of Beatles songs and will be gathered using Wikipedia’s API. We used librosa to look at waveform attributes along with Pandas to organize data into neater hierarchies. The results include a variety of visualizations showing trends by album, songwriter, vocals and more. In particular, the project was divided into sections focusing on lyrical sentiment, songwriter/vocalist analysis, album comparison, chords and chord progressions, and genre.

## Data

The primary dataset we used was all of the “main songs” performed by the Beatles, stereo remastered saved as .mp3 files. This dataset is important because it contains all 213 of the Beatles main recorded songs from albums released between 1963 and 1970, it does not include the over 100 songs released after which include live songs and unreleased songs. While many songs have many different recordings, this data set includes the stereo remastered versions of the songs which are made of the original recordings, digitally enhanced to increase the quality of the sound. We scraped this data from https://archive.org/details/thebeatlesatozsongsstereoremastered.

Secondarily, we used a dataset containing the beats, chords, keys, and structural segmentation of each song, found at http://isophonics.net/content/reference-annotations-beatles. The only songs not included in this set were "Revolution 9" and "You Know My Name (Look Up the Number)". Additionally, lyric data came from https://github.com/moizmb/beatles-lyrics and further metadata was pulled from Wikipedia.

## Code

- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/code/Audio%20Scrapping.ipynb 
This notebook has code to scrape the archive of mp3s and downloads them into a folder of all the tracks listed.
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/code/Audio%20Metadata.ipynb
This notebook scapes song metadata - that is, beats, chords, structure, and keys.
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/code/Scrape_wiki.ipynb
This notebook has code which scrapes data including songwriters, lead vocals, album, and year of release for all of the Beatles songs. 
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/code/Genre%20Scrapping.ipynb 
This gets the genre lable of the songs from wikipedia and downloads them into a csv, while this was not possible with all songs since they either don’t have a link or wikipedia page or were difficult to automate cleanly, this does get most of the songs which is enough data to train a classifier with.
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/code/Songwriters_and_LeadVocals_Comparrison.ipynb
This notebook includes code which extracts features for all of the songs using the librosa library and combines it with a cleaned version of the scraped wikipedia data(There is no code that produced this and it had to be done by hand to account for the intricacies in the differences in names between the archive dataset and the wikipedia dataset). It then creates modified versions of the Songwriters and Lead Vocals columns and plots various bivariate plots based on the features colored by the created groups for songwriters and lead vocals.
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/code/GenreClassifier.ipynb This creates a classifier that classifies the mp3s into either Rock or Psychedelia using a training set of music and outputs a graph of how songs were overall classified. 
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/code/nlp_analysis.ipynb The linked notebook first consists of sentiment analysis, specifically focusing on the lyrics over time. The second part of the notebook attempts to classify the sentiment of the lyrics based on mfccs (warning: the classifier takes 2+ hours to run).
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/code/album_analysis.ipynb This contains all the cleaning, EDA, and visualization for the album analysis. It takes 10-15 minutes to run in its entirety.

## Results

#### Lyrical Sentiment
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/results/mostcommon.png
Shows the most used words by the Beatles.
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/results/pos:neg.png
Shows the relationship between songs and their positive/negative scores.
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/results/tempo:sentiment.png
Shows the relationship between the sentiment score of the lyrics v. the song tempo.
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/results/sentimentyear.png
Shows relationship between the sentiment scores and the year.

#### Songwriters and Vocalists
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/tree/master/results/Songwriters_feature_comp 
This folder contains .png files for the plots comparing different songwriters using different features in order to identify any potential trends or differences between songs written by John Lennon and Paul McCarteny or by any other combinations. These are bivariate plots comparing spectral centroid and bandwidth, zcr and spectral bandwidth, zcr and spectral rolloff, and zcr and spectral centroid.
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/tree/master/results/Lead_Vocals_feature_comp
This folder contains .png files for the plots comparing different lead vocals using different features in order to identify any potential trends. These are bivariate plots comparing spectral centroid and bandwidth, zcr and spectral bandwidth, zcr and spectral rolloff, and zcr and spectral centroid.

#### Albums
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/tree/master/results/album_analysis
This contains two HTML files, which are the interactive Bokeh graphs describing the results of the album-wise analysis. If they’re unable to be opened properly, I also included PNG screenshots of each graph. Although these don’t have the hover tool capability to see which album each point is, I’ve listed many of the notable results in the discussion.

#### Chords
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/results/Top10Chords.png
This chart shows the top 10 chords used throughout the entire array of Beatles songs.

#### Genre
- https://github.com/ucsd-dsc-arts/dsc160-midterm-group16/blob/master/results/Rock_Psychedelia.png 
This graph shows how songs are either closer to rock or psychedelia with the year on the x axis. The higher the song is, up to 1, the more similar it is to rock and the lower it is, the more similar it is to psychedelia. This was made using the chroma_cens feature of librosa after being trained on a sample of rock and psychedelia music. Then the model classified segments of each mp3 giving it a 1 or 0 for the respective genre and then I took the average of those segments to determine the final score shown on the graph.

## Discussion

While initially we simply wanted to look at how Beatles music changed over time, we instead chose to explore variation of their music from multiple different angles, not only testing/quantifying their notable usage of Rock and Psychedelic music styles, but also looking at the changes across albums, differences between music by different songwriters and by different lead vocalists, analyzing the Beatles chord usage compared to modern day, and finally sentiment analysis based on lyrics.  

In regards to the trend over time, it seems that Rock style of music was featured prominently over the course of The Beatles’ music. What did change was the use and feature of Psychedelia in their music, in some cases tracks would contain elements of both or partially feature the use of Psychedelia rather than being totally psychedelic. This is not too surprising given the fact that the blending or use of psychedelic into their other music is a trend that has been noted before in a general sense, but the data here doesn’t show as much a trend in how the Beatles change as much as the use of it has always been around in some form or another in their music across the years with some notable exceptions. It is interesting to see this kind of result as the human mind’s tendency to find patterns in music might over exaggerate trends and this here shows only a loose trend when most people would say later career Beatles would feature Psychedelia more prominently. It might be a matter of what the Beatles got popular for over the years or there may be more discrepancy if we chart trends over months rather than years, but it's hard to judge based on the data we gathered.

When looking at the songs in terms of their albums, we found a few interesting results. Firstly, we wanted to develop certain measures by which to compare the albums. In the cleaning process, “Yellow Submarine” was omitted due to it only containing four original Beatles songs. Also omitted were any songs not directly related to any given album. The remaining 12 albums and 180 songs were then compared in terms of average unique chords per song and unique words over total words in the album, which we thought could rudimentarily represent musical and lyrical complexity, respectively. The results showed a distinct increase in musical complexity over the years, with four of their final five albums being the four most musically complex: “Abbey Road” (11/12), “Sgt. Pepper's Lonely Hearts Club Band” (8/12), “Magical Mystery Tour” (9/12), and the “White Album” (10/12). In the later years, songs began to develop more internal variation, abandoning more straightforward pop structures. The least musically complex were mostly early albums: “Please Please Me” (1/12), “Revolver” (7/12), and “With the Beatles” (2/12). The most lyrically complex were “Abbey Road”, “Sgt. Pepper’s”, and “Let It Be” (12/12). By this time, their popularity was not at stake and they tended to release songs with confusing and nonsensical lyrics, over simple lyrics about love and loss. In turn, the least lyrically complex were “A Hard Day’s Night” (3/12), “Help!” (5/12), and “Rubber Soul” (6/12).

We looked at two more features when comparing albums, both of which were developed from the MFCCs of the songs’ mp3 files. The first was “intra-album variation”, which was developed by taking the mean MFCC vector of each song on a given album, and noting each song’s distance to this mean. Essentially, how different are an album’s songs from each other? The second feature was “Album Distance From Mean”, which was intended to represent a sort-of album-wise abnormality compared to the typical Beatles song. It first took the mean MFCC vector of all 180 songs in the dataset, and then, for each album, took the average of its songs’ distances to that overall mean song.

On the intra-album variation spectrum, the clear winners were “Abbey Road”, “White Album”, and “Let It Be”, once again representing three later-era albums. Albums by that time seemed to have more structural personality, rather than maintaining one form throughout the record. In that vein, the albums with the least internal variation were “Please Please Me”, “With the Beatles”, and “Help!”. The “abnormality” spectrum was the first not to follow a direct time-linear pattern. Generally, and expectedly, the middle albums were the ones which scored the lowest on this metric. The three most “normal” were “Sgt. Pepper’s”, “Beatles For Sale” (4/12), and “Revolver”, while the three least “normal” were “A Hard Day’s Night”, “With the Beatles”, and “Abbey Road”. Fun fact: the most “Beatles-ey” Beatles song is “Piggies”, while the least “Beatles-ey” is “Revolution 9”. 

On the other hand, in regards to finding differences in music by different songwriters and lead vocalists, the exploration was mostly unfruitful. We wanted to see whether the music written by Lennon and McCartney, who wrote around ¾ of their official songs, is distinguishable from a pure audio standpoint, from songs not written by the duo, which consist of different pairs within the main 4, as well as outsiders who contributed to songwriting. Looking at the plots, we can see that there is no noticeable difference in any of 5 features between the two groups and the difference in variation is negligible. This approach had slightly better results when comparing different lead vocalists which were put into groups by each individual member, an aggregate group consisting of all mixed pairings in which the title of lead vocalist was shared, as well a final “other” category which contained their non-lyrical music. Overall while most of the plots showed no trend, one interesting result is that Songs sung by Paul McCartney seemed to have some of the lower values for mean zero-crossing rate and mean spectral centroid. While this is a small finding, it does show that in general, McCartney songs were at times, lower in pitch defined by zero-crossing rate and lower in “brightness”/timbre, defined by spectral centroid. If we were to investigate this specific area further, we would definitely implement more features, especially something like lyrics for the songwriters to see if those yield better results and see if perhaps the content between different songwriters is distinguishable.

After scraping some sites for usage of all of the Beatles’ chords in every song, we were able to perform a chord analysis. Once we combined the various csv files we extracted, it resulted in a DataFrame with the chord, the beginning time, ending time. We also needed to keep track of which song the chords came from. The conclusion from the chord analysis is that the Beatles top occurring chords throughout their career included all major scales - A, G, D, E, B, C, and F. This idea goes to show the importance of happiness and brighter tones in their music. Generally, major scales are associated with happier times, while minor scales are associated with sadness, pain, etc. This is not necessarily true, but is a common pattern in music.   

With the musical sentiment of chord structures in mind, we would be remiss if we did not also consider lyrics - half of the appeal of Beatles and rock/psychedelic songs alike - in our analysis. We wanted to see their transformation/growth through the lyrics of their songs, specifically sentiment. Upon beginning this analysis, we quickly realized that their music sentiment is quite varied by year, and that sentiment doesn’t play a major role in either genres (as in, rock and psychedelia both include positive and negative songs alike). So, we decided to take a different path, and attempted to connect sentiment to the music (rock and psychedelia) rather than lyrics. We used lyrics sentiment as a label, assuming that the lyrics represent the entire mood of the song. Then, we trained a model on all of the Beatles’ music through their mfccs to attempt to classify their sentiment score, in hopes that we could determine sentiment through music alone.

For the purpose of this project, we classified songs into three categories - positive, negative, and neutral. In the future, it would be interesting to try to determine exact sentiment scores (how positive, how negative, or how neutral). In addition, using the lyrics sentiment as an assumption of the sentiment of the entire song was quite a stretch. Having a dataset that has manually been classified would be wonderful. In addition, the classifier took around 2-3 hours to run, so learning how to more efficiently train a model would be helpful in the future when we are working with larger datasets.

The goal of this section of our project was ultimately to dig deeper into the genres of psychedelic and rock. This could be useful in many ways, such as “mood” recommendation systems on spotify. Each artist has their own style, so it is difficult to build a model for songs generally, so building a model specifically for the Beatles was thoroughly insightful. The development of quantitative measures to describe and visualize cultural phenomena was successfully prototyped through this analysis of The Beatles' catalogue.


## Team Roles

- Leon Kuo: Scrapped the m3p files and the genres from the web pages, and built a classifier for the genre based on the music. 
- Saveree Joshipura: Performed analysis on chord progressions.
- Nicole Lee: Scraped data on chords/beats and conducted sentiment analysis and classification.
- Brandon Tsui: Scraped data from wikipedia with labels for each song and performed analysis using spectral features to compare different lead vocalists as well as different songwriters.
- Will Bates: Performed album-based analysis, comparing 12 albums through features which were to be interpreted as musical and lyrical complexity, album variation, and experimentation.


## Technical Notes and Dependencies

#### Dependencies
- Jupyter Notebook
- Librosa
- Sklearn
- Bokeh
- Plotly
- Pandas
- Matplotlib
- Numpy

## Reference

References to any papers, techniques, repositories you used:

- http://isophonics.net/content/reference-annotations-beatles
- https://github.com/moizmb/beatles-lyrics
- https://archive.org/details/thebeatlesatozsongsstereoremastered
- https://en.wikipedia.org/wiki/List_of_songs_recorded_by_the_Beatles(as well as the wikipedia links of the songs that were found on here)
- https://github.com/roberttwomey/dsc160-code/blob/master/examples/audio-cluster-dim-reduction.ipynb
