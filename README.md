# Personalized Intelligent Music Selection Service

## Description
We would like to develop a **personalized intelligent music selection service** based on <mark>users' preference,  scenario,  and physiological conditions with music feature data processed through machine learning algorithm</mark>. Users may choice preferred music stream of familiar artists that are best for dancing (non-stop at a preferred tempo), or for focusing on work/study. With **physiological or environmental sensors**, music beats from stream feed may align with a user's heart beats, or music intensity/loudness match the environment's luminance  or volume.

The key challenges in the past is to have a vast music library service, algorithm analyzing audio features, a device providing physiological and environmental measurements - and we have solutions now for each.  For examples, Spotify provides [API](https://developer.spotify.com/) (both [web-based](https://developer.spotify.com/documentation/web-api/) and [Python library](https://github.com/plamere/spotipy)) for [music playback, personalized playlist, search, user taste, and audio features and analysis](https://github.com/plamere/spotipy). Personal wearable devices like Apple Watch provides heart beat and noise level measures.

## Objectives (TBD)
- Prototyping Music recommendation and selection service based on Spotify's API, particularly Features APIs that includes [danceability, tempo, energy, and valence](https://www.therecordindustry.io/analyzing-spotify-audio-features), with user text inputs (artist name, scenario or preference) on Azure Web App.
- A front-end (*web or integrated into Teams*) containing web-based player, user search (**by artist, genre, or album name**) and a list (playlist) of songs fitting to users' choice based on features. e.g.:
    - [ ] hign vibes, calm scenario relevant to **valence** in feature api.
    - [ ] playlist for dancing (**danceability**) with similar tempo (**tempo**) or vides (**valence**) through clustering algorithms (e.g. k-means) 
    - [ ]  find next optimal tracks based on currently playing (based on **tempo**, **valence**, **related artists**, **genre**) 
    - [ ] a x-y scatter plot with **tempo** and **valence** so users can choose which song to play from the interactive UI (jJvascript is better for web).
    - [ ] mapping songs with **key** and [Music Color Wheel](https://warrenmars.com/visual_art/theory/colour_wheel/music_colours/music_colours.htm) 
    - [ ] Analysis how a music is differently interpreted by artists (e.g. classical or jazee music) and more interesting data analysis with whatever tools (numpy, Excel, PoewrBI)
    
       *More details <a href="#tldr">TL;DR</a>*

- App development on smartphone and wearable devices (for example: iOS and watch OS)
- Implement own audio feature algorithm on Azure Machine Learning Service and expanding to more [musical tone characteristics](https://en.wikipedia.org/wiki/Musical_tone) such as [key](https://en.wikipedia.org/wiki/Pitch_class) and timbre.
    *Spotify API provides pitch and timbre in web api*
    *For data-lovers, check out the [json file in Teams channel](https://microsoftapc.sharepoint.com/:u:/t/Hack1963/EQ2DT4ZYPJ1CoLfJhECag-QBZZXJ4k23bBqpHp-DX4QBuA?e=xlmpbL) generated by features.py which contains Spotify feature data for* 


    ~~~~
    artist_names=[
        "Ed Sheeran",
        "The Weekend",
        "Justin Bieber",
        "Taylor Swift",
        "Eminem",
        "Adele"
    ]
    ~~~~

## Recruitment
Looking for \#Flask \#Python \#Javascript \#UX \#node.js \#React \#DataScience professionals/enthusiasts/amateurs 
(*otherwise it could just be a amateur's playground filled with json and matplotlib*)

## Resources
- [Spotify API](https://developer.spotify.com) 
   (**Note**: Subscription and developer key required)
- Python wrapper: [Spotipy](https://github.com/plamere/spotipy)
- [Spotify audio analysis samples](https://developer.spotify.com/community/showcase/spotify-audio-analysis/)



## Reference
1. [Analyzing Spotify Audio Features](https://www.therecordindustry.io/analyzing-spotify-audio-features/)

<hr>

## <a name="tldr"></a>TL;DR

Below is a sample json returned when making a search through API. With broader samples, we conclude some features are correlated (eg. "energy" and "loudness",  "tempo" and "valence", while "accusticness" and "energy" are in negative correlation). Music with 160bps temp or higher shows higher danceability particularly in western pops, and different genres of music show different patterns in scattering diagram.



and a very humble view (with Python) could be like following:
<table frame="vsides">
    <thead>
        <tr>
            <th>album</th>
            <th>name</th>
            <th>artist</th>
            <th>tempo</th>
            <th>key</th>
            <th>valence</th>
            <th>danceability</th>
            <th>popularity</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><a href="https://open.spotify.com/track/5m1i6hq7dmRlp3c1utE48L"><img src="https://i.scdn.co/image/ab67616d000048512c34b754c9f4fb50c37e6982"></a></td>
            <td><a href="https://open.spotify.com/track/5m1i6hq7dmRlp3c1utE48L">水平線</a></td>
            <td><a href="https://open.spotify.com/artist/6rs1KAoQnFalSqSU4LTh8g">back number</a></td>
            <td>145.867</td>
            <td>10</td>
            <td>0.436</td>
            <td>0.419</td>
            <td>73</td>
        </tr>
        <tr>
            <td><a href="https://open.spotify.com/track/3f4fc8c8unrQeKecmUPEDR"><img src="https://i.scdn.co/image/ab67616d00004851f8fa082806184fcb032d8e0a"></a></td>
            <td><a href="https://open.spotify.com/track/3f4fc8c8unrQeKecmUPEDR">Warriors</a></td>
            <td><a href="https://open.spotify.com/artist/47mIJdHORyRerp4os813jD">League of Legends</a></td>
            <td>185.121</td>
            <td>1</td>
            <td>0.0412</td>
            <td>0.14</td>
            <td>70</td>
        </tr>
        <tr>
            <td><a href="https://open.spotify.com/track/29Y7wbrOvQlAwZQJM51ugW"><img src="https://i.scdn.co/image/ab67616d00004851f2a5b943d459d18e68a52801"></a></td>
            <td><a href="https://open.spotify.com/track/29Y7wbrOvQlAwZQJM51ugW">Survivor</a></td>
            <td><a href="https://open.spotify.com/artist/4SGDDnlwi5G42HTGzYl2Fc">2WEI</a></td>
            <td>132.941</td>
            <td>7</td>
            <td>0.0947</td>
            <td>0.348</td>
            <td>68</td>
        </tr>
        <tr>
            <td><a href="https://open.spotify.com/track/6ts1KCOudfDYXYfyWtq0k1"><img src="https://i.scdn.co/image/ab67616d00004851ac1a5a83790ba13920affe1e"></a></td>
            <td><a href="https://open.spotify.com/track/6ts1KCOudfDYXYfyWtq0k1">おもかげ (produced by Vaundy)</a></td>
            <td><a href="https://open.spotify.com/artist/45ft4DyTCEJfQwTBHXpdhM">milet</a></td>
            <td>207.906</td>
            <td>8</td>
            <td>0.713</td>
            <td>0.488</td>
            <td>66</td>
        </tr>
        <tr>
            <td><a href="https://open.spotify.com/track/10Eyo4juZQFthKqlJgGMdp"><img src="https://i.scdn.co/image/ab67616d00004851ae51734d04ef431b65a09a9a"></a></td>
            <td><a href="https://open.spotify.com/track/10Eyo4juZQFthKqlJgGMdp">怪盗</a></td>
            <td><a href="https://open.spotify.com/artist/6rs1KAoQnFalSqSU4LTh8g">back number</a></td>
            <td>114.028</td>
            <td>7</td>
            <td>0.8</td>
            <td>0.636</td>
            <td>64</td>
        </tr>
        <tr>
            <td><a href="https://open.spotify.com/track/3l2O4IuJ4DFEfUwDdWyPnf"><img src="https://i.scdn.co/image/ab67616d000048515083e995f26ad0e8915cf876"></a></td>
            <td><a href="https://open.spotify.com/track/3l2O4IuJ4DFEfUwDdWyPnf">Walkin' In My Lane</a></td>
            <td><a href="https://open.spotify.com/artist/45ft4DyTCEJfQwTBHXpdhM">milet</a></td>
            <td>190.107</td>
            <td>7</td>
            <td>0.342</td>
            <td>0.604</td>
            <td>63</td>
        </tr>
        <tr>
            <td><a href="https://open.spotify.com/track/2jdbZGFp8KVTuk0YxDNL4l"><img src="https://i.scdn.co/image/ab67616d00004851783ed3c2af46af7ab7c671c0"></a></td>
            <td><a href="https://open.spotify.com/track/2jdbZGFp8KVTuk0YxDNL4l">高嶺の花子さん</a></td>
            <td><a href="https://open.spotify.com/artist/6rs1KAoQnFalSqSU4LTh8g">back number</a></td>
            <td>137.977</td>
            <td>9</td>
            <td>0.343</td>
            <td>0.54</td>
            <td>63</td>
        </tr>
        <tr>
            <td><a href="https://open.spotify.com/track/4FMz2RFrbDGzJO7K4D0vS3"><img src="https://i.scdn.co/image/ab67616d00004851ce51ffc5c742ed217779cb9d"></a></td>
            <td><a href="https://open.spotify.com/track/4FMz2RFrbDGzJO7K4D0vS3">HAPPY BIRTHDAY</a></td>
            <td><a href="https://open.spotify.com/artist/6rs1KAoQnFalSqSU4LTh8g">back number</a></td>
            <td>145.988</td>
            <td>11</td>
            <td>0.535</td>
            <td>0.482</td>
            <td>62</td>
        </tr>
        <tr>
            <td><a href="https://open.spotify.com/track/2iI556oF2qwtac9r1RzrXo"><img src="https://i.scdn.co/image/ab67616d00004851550c8aec89803c37428579b6"></a></td>
            <td><a href="https://open.spotify.com/track/2iI556oF2qwtac9r1RzrXo">The Call</a></td>
            <td><a href="https://open.spotify.com/artist/47mIJdHORyRerp4os813jD">League of Legends</a></td>
            <td>132.709</td>
            <td>5</td>
            <td>0.115</td>
            <td>0.203</td>
            <td>62</td>
        </tr>
    </tbody>
</table>