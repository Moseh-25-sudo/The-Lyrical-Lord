# ![Logo](https://i.imgur.com/U9YCwwT.png) 

[Lyrics For Learning](http://lyricsforlearning.net/) is a web application aimed at helping students practice their English language skills through music. Upon visiting the site, you can select a popular song and explore the meaning of words within the lyrics. Specifically, you can check out a linguistic breakdown of each word and share what you think the word means within the context of the song.


## Table of content

- [Inspiration](#inspiration)
- [Built With](#built-with)
- [Getting Started](#getting-started)
- [Features](#features)
    - [Song Selection](#song-selection)
    - [Words To Explore](#words-to-Explore)
    - [Linguistic Breakdown and Highlighting Of Selected Words](#linguistic-breakdown-and-highlighting-of-selected-words)
    - [Submit interpretations and view past submissions](#submit-interpretations-and-view-past-submissions)
    - [Suggest a Song Form](#suggest-a-song)
- [API](#API)
- [Future](#future)
- [Attributions](#attributions)
- [Author](#author)

## Inspiration

The inspiration behind the project was based on the fact that I had a thought about how useful it would have been if I had such an app as I tried to learn a foreign language online. I saw it easier learning through lyrics from songs in different languages and learning the meaning of the words used, their pronunciations and antonation when using the words during communication.

## Built With

### Tools

# ![Tools](https://i.imgur.com/vKyy1ZR.png)

### Architecture

# ![Architecture](https://i.imgur.com/E3TaTuX.png)

## Getting Started

To start using this web application, visit lyricsforlearning.net. To install it, simply clone this repository. You can start the app by running `web_app.app` and `api.v1.app` as Python modules in separate terminal windows. Please note, in order to run this app, you will need to install necessary dependencies as well as pass in the correct MySQLdb and Words API credentials respectively.

## Features

### **Song selection**

Lyrics For Learning provides a selection of "clean" and vocabulary-rich songs to explore from a variety of different genres. The data for each song is fetched from the internal RESTful API and is used to fill each Bootstrap card. The song's id is used as the id for the "View" button within the song's card. This allows for the correct song details to be fetched when the user clicks on the button since the id becomes part of the URL for the song.

# ![song-selection](https://i.imgur.com/h3m9fko.png)

### **Words To Explore**

When a user selects a song, they are re-directed to a song-specific page where the song's details are fetched from the internal RESTful API. This includes a list of words to explore that appear in the lyrics for the song. Event listeners are setup on each word so that the linguistic breakdown of it can be fetched from an external API and so that it can be highlighted within the lyrics.

# ![words-to-explore](https://i.imgur.com/JBlT2hx.png)

### **Linguistic Breakdown and Highlighting of Words**


The external Words API is accessed to retrieve the linguistic breakdown when a user chooses a particular word from a song. After that, a menu will be created by the JS script depending on how many items are available for the word. The script will then determine which parts are available for an entry (such as "Definition," "Synonyms," or "Examples") when a user clicks on it. The user can browse a dynamic tabbed interface filled with the accessible sections and their contents. Furthermore, the lyrics highlight the term. By first analyzing the lyrics and inserting span elements around words that show up in the "Pick a word to explore!" list, this was made possible. Aligned classes have been added to the spans so they can be chosen so that it can be noticed and targeted.

# ![linguistic-breakdown-and-highlighting-of-words](https://i.imgur.com/YKhWuCj.png)

### **Submit Interpretations and View Past Interpretations**

The user can contribute their interpretation of the artist's meaning behind a word after studying its grammatical breakdown. Their interpretation is provided as a `POST` request to the internal RESTful API when they click "Submit". The interpretation is then checked for profanity using the `better-profanity` module; if it is, the contribution is not saved in the database and the user is shown with a warning popup. The input is kept in the database and viewed in the accordian-style "Latest Interpretations" section if it contains no profanity.

# ![submit-interpretations-and-view-past-interpretations](https://i.imgur.com/lAmK39I.png)

### **Suggest a Song Form**

A user can visit the "Suggest a Song" page and complete the form if they would like to recommend a song to be added to the library of songs to learn from. The artist, title, and words to be learned from the song are among the details the form will need in order to create a new Song object. In order to earn credit for their contribution and to be alerted when the song is added to the collection, the user must additionally provide their name and email address.

# ![suggest-a-song-form](https://i.imgur.com/jspGhrb.png)

## API

I built an internal RESTful API for this web application so that data can be flexibly retreived from the MySQLdb. All available endpoints can be found in the `api.v1.views` directory. Here's a description of each endpoint:

/api/v1/interpretations/<word_id>/<song_id>

* GET: Retrieves all Interpretation objects for a word from a song and returns a list containing
    all of them
    
* POST: Creates an interpretation for a word from a song

/api/v1/interpretations/<interpretation_id>

* PUT: Updates an Interpretation object

/api/v1/songs/<song_id>/words

* GET: Retrieves all words from a song and returns a list containing
    all of them

/api/v1/songs

* GET: Retrieves all Song objects from database and returns a list containing
    all of them

/api/v1/songs/<text>
  
* GET: Retrieves Song object from database and returns a dictionary

/api/v1/songs/genre/<genre>
  
* GET: Retrieves all Song objects from database with a specified genre

/api/v1/suggestions/

* GET: Retrieves all Suggestion objects from database and returns a list containing
    all of them
    
* POST: Creates a Suggestion object

/api/v1/words/<text>
  
* GET: Retrieves word_id based on word

/api/v1/words_api/<text>

* GET: Retrieves data for word from external API and returns response to client-side.
     By passing in API credentials from the command line when running the API and 
     using the internal API for the fetch, it prevents credentials from being exposed
     on the front-end.
     
## Future

The Lyrical Lord has a lot more features that I would like to add in the future, beyond this original MVP that was created in just two weeks. I want to build up an authentication system specifically. Along with this, I would also like to make it possible for users to create profiles, which would allow them to view their previous progress and further customize the experience by offering phrases and songs to listen to or explore depending on previous usage. Furthermore, I would like to enable people to modify previously submitted work and to support and encourage one another's interpretations. Additionally, I'm thinking about including a "Top Users" board on the front page.

Please don't hesitate to get in touch with me if you would want to help to this project or if you have any suggestions for features.


## Attributions

Shout-out to [Open Lyrics Database](https://github.com/Lyrics/lyrics) for the lyrics shown!

Licenses for images from Wikimedia Commons:

* [The xx at the Alcatraz.jpg](https://commons.wikimedia.org/wiki/File:The_xx_at_the_Alcatraz.jpg)
* [Adele Live 2016 tour.jpeg](https://commons.wikimedia.org/wiki/File:Adele_Live_2016_tour.jpeg)
* [Paul Simonon The Clash September 20 1979 Palladium NYC.jpg](https://commons.wikimedia.org/wiki/File:Paul_Simonon_The_Clash_September_20_1979_Palladium_NYC.jpg)

## Author
### **Moses Ng'ang'a**

[Github](https://github.com/Moseh-25-sudo)
[LinkedIn](https://www.linkedin.com/in/SEMosesNganga)
