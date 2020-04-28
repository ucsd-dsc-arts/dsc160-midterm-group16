# Project Title

DSC160 Data Science and the Arts - Midterm Project Repository - Spring 2020

Project Team Members: 
- Leon Kuo, lkuo@ucsd.edu
- Will Bates, wbates@ucsd.edu
- Saveree Joshipura, sjoshipu@ucsd.edu
- Nicole Lee, nml015@ucsd.edu
- Brandon Tsui, bhtsui@ucsd.edu

Ideas and Scheduling Doc: https://docs.google.com/document/d/1kLNA6V-ilkDmu5EcxvhBqU_WcHCIoU4yQ6_n61uY4y0/edit?usp=sharing

## Abstract

(10 points) 

People believe that throughout the years, The Beatles’ music transitioned from classic popular music to experimental music. We predict this is a true statement, and aim to quantify this transition. The goal of our project will be to answer the following question: what features and/or trends defined eras of The Beatles’ music, and how can we visually display that? Our dataset will consist of all The Beatles’ songs. There are roughly 230 songs. Our group finds a personal interest in this project, as we are all Beatles fans. Performing analysis on their music is fascinating for many reasons, especially quantifying their transition from popular music to experimental music and seeing the defining features and trends of each era.

We will use BeautifulSoup to scrape the audio from https://archive.org/details/thebeatlesatozsongsstereoremastered and plan to focus on using features such as complexity score, MFCC, beats per minute/tempo of the song, chord types (major/minor), and release year of each song. The labels will come from a Wikipedia list of Beatles songs and will be gathered using Wikipedia’s API. We’ll likely be using librosa to look at waveform attributes along with other software tools such as numpy and Pandas to organize data into neater hierarchies. The results are going to be in the form of a graph that shows their shift over time from their original style of music to the more psychedelic music. A scatter plot will most likely be used to place each of their songs on a graph. We aim to use Bokeh plots to show visualizations from the beginning of their career to the end, using the cover of each album to go along with the year of its release. We will be utilizing feature extraction tools that we have used in class (MFCCs, etc), determining different features that most effectively define the change in The Beatles’ music. In addition, we will take inspiration from visualizations shown in class to present the results of our findings.

## Data

(10 points) 

This section will describe your data and its origins. Each item should contain a name of the data source, a link to the source, and any necessary background information such as:
- What is your cultural data source? 
- When was it made? 
- Who created the works? 
- Is it digital native, or is it some kind of scan, recording, photo, etc., of an analog form? 

## Code

(20 points)

This section will link to the various code for your project (stored within this repository). Your code should be executable on datahub, should we choose to replicate your result. This includes code for: 

- data acquisition/scraping
- cleaning
- analysis
- generating results. 

Link each of your notebooks or .py files within this section, and provide a brief explanation of what the code does. Reading this section we should have a sense of how to run your code.

## Results

(30 points) 

This section will contain links to documentation of your results. This can include figures, sound files, videos, bitmaps, as appropriate to your domain of analysis. Each result should include a brief textual description, and all should be listed below: 

- image files (`.jpg`, `.png` or whatever else is appropriate)
- audio files (`.wav`, `.mp3`)
- written text as `.pdf`

## Discussion

(30 points, three to five paragraphs)

The first paragraph should be a short summary describing your results.

The subsequent paragraphs could address questions including:
- Why is this culturally relevant?
- How does your computational approach differ from the traditional art historical, musicological, manuel/subjective approach to analyzing your cultural subject? 
- How do you think the original artists/musicians would respond to this type of analysis? Would it change/inform their practice in some way?
- How do your results relate to broader social, cultural, economic political, etc., issues? 
- In what future directions could you expand this work?

## Team Roles

Provide an account of individual members and their efforts/contributions to the specific tasks you accomplished.

## Technical Notes and Dependencies

Any implementation details or notes we need to repeat your work. 
- Additional libraries you are using for this project
- Does this code require other pip packages, software, etc?
- Does this code need to run on some other (non-datahub) platform? (CoLab, etc.)

## Reference

References to any papers, techniques, repositories you used:
- Papers
- Repositories
- Blog posts
