# Pylyrics  
A Python package to extract and analyze lyrics

-   Authors: Abhiket Gaurav, Artan Zandian, Macy Chan, Manju Abhinandana Kumar

<br>

### Overview
This package allows users to extract and analyze lyrics effortlessly. With pylrics users can download songs attribute datasets from Kaggle, extract lyrics and generate a word cloud. 

<br>

### Functions
---
<br>

| Function Name | Input | Output | Description |
|-----------|------------|---------------|------------------|
| download_data | `dataset`, `file_path`, `columns` | Pandas Dataframe | Downloads dataset `dataset` from kaggle and extract `columns` from csv file |
| extract_lyrics | `token`, `song_title`, `artist` | String | Extracts song lyrics of a song `song_title` by `artist` using `token` |
| clean_text | `lyrics` | String |  Cleans up the `lyrics` by removing special characters, html tags, #tags, contaction words |
| plot_cloud | `song`, `file_path`, `max_font_size`, `max_words`, `background_color`, `show` | Image | Creates a word cloud image of most occuring words of a song/songs by an artist |


### Our Package in the Python Ecosystem
---
There exist similar packages Python. However, this package is more holistic, in the sense that it downloads the lyrics through APIs, cleans the text, and then makes the word cloud. There are packages which does one of these steps. This package takes care of all the steps. Of the many other similar packages, the following are the two examples that come close: https://github.com/lorenza12/Cloud-Lyrics and https://deezer.io/a-new-way-to-look-at-an-artist-from-lyrics-to-wordclouds-christmas-special-56a854cb4e77#.op1gx82h4



### Installation
---
```bash
$ pip install pylyrics
```
<br>

### Features
The pylyrics packages contains the following four functions:

1. `download_data()` The download data function downloads dataset from Kaggle, extracts the given columns from csv file and creates a dataframe.

2. `extract_lyrics()` The extract lyrics function, extracts the lyrics from API for a song title and artist and saves as String.

3. `clean_text()` The lyrics extracted from extract_lyrics() are not clean. It removes special characters, html tags, #tags, contaction words to get a cleaned paragraph. 

4. `plot_cloud` The plot cloud function creates a word cloud of most occuring words in a song/songs by an artist.

<br>

### Dependencies
---
- python = ^3.9
- pandas = ^1.2.3
- regex
- kaggle
- json
- urllib.parse
- lyricsgenius
- alive_progress
- wordcloud
- matplotlib  
<br>

### Usage
---
#### Downloading and Selecting
The first function in our package is the `download_data()`. Here you will input your `kaggle dataset` and the columns to be extracted into a Pandas DataFrame with `cols` argument. 

To use the Kaggle API, sign up for a Kaggle account at https:/www.kaggle.com. Then go to the 'Account' tab of your user profile (https:/www.kaggle.com/\<username\>/account) and select 'Create API Token'. This will trigger the download of kaggle.json, a file containing your API credentials. Place this file in the location `~/.kaggle/kaggle.json`. The function will automatically read your Kaggle credentials from the above path.
  
```python 
from pylyrics import download_data
# Example dataset: Spotify Song Attributes  
dataset = "geomack/spotifyclassification"
# Extract columns 
df_columns = pylyrics.download_data(dataset, cols=['energy', 'liveness'])
```
#### Extracting Lyrics
The `extract_lyrics()` function gets the `song_title` and `artist` name, checks validity and avialability of the combination, and extracts the lyrics for that song in a raw string format with header, footer etc which needs to be cleaned in order to create a human-readable text.  
```python 
from pylyrics import extract_lyrics
# extracting lyrics 
raw_lyrics = pylyrics.extract_lyrics(song_title, artist)
```
#### Cleaning
Our `clean_text()` function is straightforward tool to clean the input data and make the text human-readable.
```python 
from pylyrics import clean_text
# Clean the extracted raw lyrics (paragraph)
clean_lyrics = pylyrics.clean_text(paragraph, vocabs)
```

#### Creating WordCloud
WordCloud is an artistic rendering of the most frequent words in a text document. A higher occurrence for a word is translated into a larger text size.  
At this stage, we have helper functions to facilitate the extraction and cleaning of lyrics. The `plot_cloud()` function accepts a **dictionary** with `artist` as dictionary key and `song_title` as values. It will then extract the lyrics for all songs in the dictionary and saves a WordCould of the most occurring terms in the `file_path` provided by the user. You may specify if you want to see the output plot by setting `show=True`. The WordClould parameters to be set are self-explanatory: `max_font_size`, `max_word` and `background_color`.
```python 
from pylyrics import plot_cloud
# plotting and saving WordCloud
pylyrics.plot_cloud(song,
    file_path, max_font_size=30, max_words=120, background_color="black", show=False)
```

<br>

### Documentation
---
The official documentation is hosted on Read the Docs: [Link TBC]

<br>

## Contributors
---
The names of core development team is listed below.

| Name |
|------|
| Abhiket Gaurav |  
| Artan Zandian | 
| Macy Chan | 
| Manju Abhinandana Kumar |  

We welcome and recognize all contributions. Check out the contributing guidelines. Please note that this project is released with a Code of Conduct. By contributing to this project, you agree to abide by its terms.

### License

`pylyrics` was created by Group 2. It is licensed under the terms of the MIT license.

### Credits

`pylyrics` was created with [`cookiecutter`](https://cookiecutter.readthedocs.io/en/latest/) and the `py-pkgs-cookiecutter` [template](https://github.com/py-pkgs/py-pkgs-cookiecutter).
