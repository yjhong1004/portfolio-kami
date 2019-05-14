---
layout: post
title: BlocJams
thumbnail-path: "img/blocitoff.png"
short-description: Build a digital music player, similar to Spotify.

---

{:.center}
![]({{ site.baseurl }}/img/blocitoff.png)

## Explanation

We will be utilizing front end technologies to develop a music player, similar to Spotify. We'll start by creating a skeleton structure of the app, using HTML. We'll add styling and responsiveness using CSS. Lastly, we'll increase interactivity with Javascript.

## Problem

Complete these objectives:
1. Include CSS in an HTML document using external stylesheets.
2. Utilize normalize.css
3. Add classes to HTML tags and use class names to style elements.
4. Identify selectors, properties, and values in a CSS file.
5. Recognize HTML attributes – such as rel, type, href, src, etc. – and discuss the purpose of common attributes.

## Solution

Basic HTML Structure that we start off with:

```
<html>
    <head>
        <title>Bloc Jams</title>
        <link rel="stylesheet" type="text/css" href="http://fonts.googleapis.com/css?family=Open+Sans:400,800,600,700,300">
        <link rel="stylesheet" type="text/css" href="http://code.ionicframework.com/ionicons/2.0.1/css/ionicons.min.css">
        <link rel="stylesheet" type="text/css" href="styles/normalize.css">
        <link rel="stylesheet" type="text/css" href="styles/main.css"
    </head>
    <body class="landing">
        <nav class="navbar">
          <img src="assets/images/bloc_jams_logo.png" alt="bloc jams logo" class="logo"> <!-- navigation bar -->
        </nav>
        <section class="hero-content">
                <h1 class="hero-title">Turn the music up!</h1>
        </section>
        <section class="selling-points">
            <div class="point">
                <span class="ion-music-note"></span>
                <h5 class="point-title">Choose your music</h5>
                <p class="point-description">The world is full of music; why should you have to listen to music that someone else chose?</p>
            </div>
            <div class="point">
                <span class="ion-radio-waves"</span>
                <h5 class="point-title">Unlimited, streaming, ad-free</h5>
                <p class="point-description">No arbitrary limits. No distractions.</p>
            </div>
            <div class="point">
                <span class="ion-iphone"</span>
                <h5 class="point-title">Mobile enabled</h5>
                <p class="point-description">Listen to your music on the go. This streaming service is available on all mobile platforms.</p>
            </div>
        </section>
```
Notice that we utilized normalize.css. This is because each browser renders certain styles differently. We use this neat trick to make browsers render all elements in line with modern standards.

We now have our basic layout of our website. We split the landing page into different sections to organize our code properly. We have our navigation bar at the top of the page. We also have our "hero" container, which will be in the middle of our page. This is intentional as we want this section to be shown in greater detail. Lastly, we have our selling points section, which holds different icons. The selling points section is also split into three event sections, each representing different information about our application.

Basic CSS styling to bring some color into our app:

```
html {
    height: 100%; /* makes sure our HTML takes up 100% of the browser window */
    font-size: 100%;
}

body {
    font-family: 'Open Sans'; /* sets our font to the "Open Sans" typeface */
    color: white;             /* sets the text color to white */
    min-height: 100%;         /* says the height of the body must be, at minimum, 100% of the window */
}

body.landing {
    background-color: rgb(58,23,63); /* sets the background color to an RGB value (see below) */
}

 .navbar {
     padding: 0.5rem;
     background-color: rgb(101,18,95);
 }

 .navbar .logo {
     position: relative; /* positioning will be explained in a resource */
     left: 2rem;
 }

 .hero-content {
     position: relative; /* positioning will be explained in a resource */
     min-height: 600px;  /* hero content element must be _at least_ 600 pixels */
     background-image: url(../assets/images/bloc_jams_bg.jpg);
     background-repeat: no-repeat;
     background-position: center center;
     background-size: cover;
 }

 .hero-content .hero-title {
     position: absolute;             /* positioning will be explained in a resource */
     top: 40%;                       /* positioning will be explained in a resource */
     -webkit-transform: translateY(-50%);
     -moz-transform: translateY(-50%);
     -ms-transform: translateY(-50%);
     transform: translateY(-50%);
     width: 100%;                    /* makes sure the title inhabits the full width of its container */
     text-align: center;             /* aligns text in the horizontal center of the element */
     font-size: 4rem;                /* specifies the size of the font in root em units */
     font-weight: 300;               /* makes the font thinner or lighter weight */
     text-transform: uppercase;      /* transforms the text to be all uppercase lettering */
     letter-spacing: 0.5rem;         /* puts 0.5 root ems worth of space between each letter */
     text-shadow: 1px 1px 0px rgb(58,23,63); /* creates a shadow underneath the text for readability over the image */
 }

 .selling-points {
     position: relative;
     display: table;
     width: 100%;
     -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
     box-sizing: border-box; /* we'll explain this in a resource */
 }

 .point {
     display: table-cell;
     position: relative;
     width: 33.3%;
     padding: 2rem;
     text-align: center;
 }

 .point .point-title {
     font-size: 1.25rem;
 }

 .ion-music-note,
 .ion-radio-waves,
 .ion-iphone {
     color: rgb(233,50,117);
     font-size: 5rem;
```
We want to make sure that our website is accessible on all devices and shown properly on all screen sizes. We set the viewport meta tag in our <head> tag, which indicates how the browser should render the content in the device's window.

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```
We also want to add media queries, which will help us apply styles conditionally and by utilizing parameters.

```
 /* Medium and small screens (640px) */
 @media (min-width: 640px) {
    html { font-size: 112%; }
    .column {
          float: left;
          padding-left: 1rem;
          padding-right: 1rem;
    }

    .column.full { width: 100%; }
    .column.two-thirds { width: 66.7%; }
    .column.half { width: 50%; }
    .column.third { width: 33.3%; }
    .column.fourth { width: 25%; }
    .column.flow-opposite { float: right; }
 }
 /* Large screens (1024px) */
 @media (min-width: 1024px) {
   html { font-size: 120%; }

 }
```
Let's continue customizing our application to fit different media devices.
Since bigger screens would cause our application to stretch, we want to set a max-width on a container to make sure our website looks like how we designed it to look.

```
.container {
     margin: 0 auto;
     max-width: 64rem;
 }
```
Remember to attach our container class to our .selling-points section.
```
<section class="selling-points container">
```

Now that we have our responsive design implemented, we want to go ahead and continue with the building of our application. We want to start with creating a skeleton page for our collection of music.

```
<section class="album-covers container clearfix">
        <div class="collection-album-container column fourth">
            <img src="assets/images/album_covers/01.png"/>
            <div class="collection-album-info caption">
                <p>
                    <a class="album-name" href="#">The Colors</a>
                    <br/>
                    <a href="#">Pablo Picasso</a>
                    <br/>
                    X songs
                    <br/>
                </p>
            </div>
        </div>
...

```

Of course, we want to style our skeleton in our collection.css file.

```
body.collection {
    background-image: url(../assets/images/blurred_backgrounds/blur_bg_2.jpg);
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: center center;
    background-size: cover;
}
...
```
Once we have our collection view, we want to work on our album view, which allows a user to view the details of a single album.

We create a skeleton of the album detail page. Then, we add a section for the album cover image, title, artist, and release information.

```
<main class="album-view container narrow">
             <section class="clearfix">
                 <div class="column half">
                     <img src="assets/images/album_covers/01.png" class="album-cover-art">
                 </div>
                 <div class="album-view-details column half">
                     <h2 class="album-view-title">The Colors</h2>
                     <h3 class="album-view-artist">Pablo Picasso</h3>
                     <h5 class="album-view-release-info">1909 Spanish Records</h5>
                 </div>
             </section>
         </main>
```

Notice that we utilize syntactic tags. The <main> tag is used for the main content.

Let's add some styles to our album page.

```
...

.album-cover-art {
     position: relative;
     left: 20%;
     margin-top: 1rem;
     width: 60%;
 }

 .album-view-details {
     position: relative;
     top: 1.5rem;
     padding: 1rem;
 }
...
```

We want to add song listings to our album skeleton. We utilize the <table> tag to add the details.

```
<main class="album-view container narrow">
    <section class="clearfix">
        ...
    </section>
    <table class="album-view-song-list">
        <tr class="album-view-song-item">
            <td class="song-item-number">1</td>
            <td class="song-item-title">Blue</td>
            <td class="song-item-duration">X:XX</td>
        </tr>
...
```
Keep in mind that this is just the structure with placeholder album data, which we will use with real data.

We also want to style our details in our album.css file. We also want to make our album view responsive, using media queries.

```
.album-view-song-list {
     width: 90%;
     margin: 1.5rem auto;
     font-weight: 300;
     font-size: 0.75em;
     border-collapse: collapse;
 }
...

@media (max-width: 640px) and (min-width: 320px) {
     .album-view-details {
         text-align: center;
     }

     .album-view-title {
         margin-top: 0;
     }
 }
```

At this point of our project, we will be moving onto vanilla Javascript, called DOM Scripting.

We will use CSS transitions to animate between properties to change an element's appearance.

Remember our selling points on our landing page?

```
.point {
    position: relative;
    padding: 2rem;
    text-align: center;
    opacity: 0;
    -webkit-transform: scaleX(0.9) translateY(3rem);
    -moz-transform: scaleX(0.9) translateY(3rem);
    transform: scaleX(0.9) translateY(3rem);
    -webkit-transition: all 0.25s ease-in-out;
    -moz-transition: all 0.25s ease-in-out;
    transition: all 0.25s ease-in-out;
    -webkit-transition-delay: 0.2s;
    -moz-transition-delay: 0.2s;
    transition-delay: 0.2s;
}
```
We write Javascript to trigger the animations.

```
  var pointsArray = document.getElementsByClassName('point');
  var revealPoint = function (point) {
    point.style.opacity = 1;
    point.style.transform = "scaleX(1) translateY(0)";
    point.style.msTransform = "scaleX(1) translateY(0)";
    point.style.WebkitTransform = "scaleX(1) translateY(0)";
    }

  function forEach (array, callback) {
   for (var i = 0; i < array.length; i++) {
     callback(array[i]);
   }
  }
  var animatePoints = function(points) {
    forEach(points, revealPoint);
  };

```

The animatePoints() function will activate the CSS transitions and update the styles from what we've placed in the CSS file to the new styles in the script.
Our application should know when to trigger the animations. This concept is called DOM event.

We first add an event that detects the page load. This is done through a properly called onload. The function that handles code in response to an event is called the event handler.
Then, we want to attach a behavior to the scroll event. We call the addEventListener function to add a listener to the window object. We want our animatePoints() function to run when the user scrolls the selling points into view. We also want to take into account taller screens, which can display all the content on load. So we make sure we can animate the selling points immediately without the need for a scroll event.

```
window.onload = function() {
    if (window.innerHeight > 950) {
        animatePoints(pointsArray);
    }
    var sellingPoints = document.getElementsByClassName('selling-points')[0];
    var scrollDistance = sellingPoints.getBoundingClientRect().top - window.innerHeight + 200;
    window.addEventListener('scroll', function(event) {
        if (document.documentElement.scrollTop || document.body.scrollTop >= scrollDistance) {
            animatePoints(pointsArray);
        }
    });
}
```
Currently, our collection view displays static placeholders. We would need to create a script that dynamically generates as many albums as needed to display.

From our collection.html, we need to remove our static templates.
We replace this with a template.

```
var collectionItemTemplate =
    '<div class="collection-album-container column fourth">' +
    '  <img src="assets/images/album_covers/01.png"/>' +
    '  <div class="collection-album-info caption">' +
    '    <p>' +
    '      <a class="album-name" href="album.html"> The Colors </a>' +
    '      <br/>' +
    '      <a href="album.html"> Pablo Picasso </a>' +
    '      <br/>' +
    '      X songs' +
    '      <br/>' +
    '    </p>' +
    '  </div>' +
    '</div>';
```
Then, we add a function to automatically generate the album data template.
```
window.onload = function() {
    var collectionContainer = document.getElementsByClassName('album-covers')[0];
    collectionContainer.innerHTML = '';
    for (var i = 0; i < 12; i++) {
        collectionContainer.innerHTML += collectionItemTemplate;
    }
}
```
We do a similar thing with the album.html file. We remove the static elements and use Javascript to dynamically add information.
In our album.js file, we add some example album information.

```
var albumPicasso = {
     title: 'The Colors',
     artist: 'Pablo Picasso',
     label: 'Cubism',
     year: '1881',
     albumArtUrl: 'assets/images/album_covers/01.png',
     songs: [
         { title: 'Blue', duration: '4:26' },
         { title: 'Green', duration: '3:14' },
         { title: 'Red', duration: '5:01' },
         { title: 'Pink', duration: '3:21'},
         { title: 'Magenta', duration: '2:15'}
     ]
};
```
In a real world situation, we would be pulling information from a database.

We create a function, createSongRow, that generates song row content.
```
var createSongRow = function(songNumber, songName, songLength) {
     var template =
        '<tr class="album-view-song-item">'
      + '  <td class="song-item-number">' + songNumber + '</td>'
      + '  <td class="song-item-title">' + songName + '</td>'
      + '  <td class="song-item-duration">' + songLength + '</td>'
      + '</tr>'
      ;

     return template;
};
```

We create a function, setCurrentAlbum, that will be called when the window loads. It takes one of our album objects and injects it into the template.

```
var setCurrentAlbum = function(album) {
    var albumTitle = document.getElementsByClassName('album-view-title')[0];
    var albumArtist = document.getElementsByClassName('album-view-artist')[0];
    var albumReleaseInfo = document.getElementsByClassName('album-view-release-info')[0];
    var albumImage = document.getElementsByClassName('album-cover-art')[0];
    var albumSongList = document.getElementsByClassName('album-view-song-list')[0];

    albumTitle.firstChild.nodeValue = album.title;
    albumArtist.firstChild.nodeValue = album.artist;
    albumReleaseInfo.firstChild.nodeValue = album.year + ' ' + album.label;
    albumImage.setAttribute('src', album.albumArtUrl);
    albumSongList.innerHTML = '';

    for (var i = 0; i < album.songs.length; i++) {
        albumSongList.innerHTML += createSongRow(i + 1, album.songs[i].title, album.songs[i].duration);
    }
};

window.onload = function() {
    setCurrentAlbum(albumPicasso);
}
```

Now, we will be getting into the details of our application. We will be implementing functions for play and pause buttons on our album page.

We want to implement event delegation, which allows us to listen for an event on a parent element but target the behavior on its children.

```
var songListContainer = document.getElementsByClassName('album-view-song-list')[0];
var songRows = document.getElementsByClassName('album-view-song-item');
var playButtonTemplate = '<a class="album-song-button"><span class="ion-play"></span></a>';
window.onload = function() {
        setCurrentAlbum(albumPicasso);

        songListContainer.addEventListener('mouseover', function(event) {
            // #1
            if (event.target.parentElement.className === 'album-view-song-item') {
                event.target.parentElement.querySelector('.song-item-number').innerHTML = playButtonTemplate;
            }
        });
        for (var i = 0; i < songRows.length; i++) {
            songRows[i].addEventListener('mouseleave', function(event) {
                this.children[0].innerHTML = this.children[0].getAttribute('data-song-number');
            });
        }
```
We use mouseleave event to signal when a mouse leaves the target element. We want to be as specific to the cell as possible, so we attach event listeners to each table row instead of using event delegation.

We add a play button template and add some styling to it.
```
var playButtonTemplate = '<a class="album-song-button"><span class="ion-play"></span></a>';
```
```
.album-song-button {
     text-align: center;
     font-size: 14px;
     background-color: white;
     color: rgb(210, 40, 123);
     border-radius: 50% 50%;
     display: inline-block;
     width: 28px;
     height: 28px;
 }

 .album-song-button:hover {
     cursor: pointer;
     color: white;
     background-color: rgb(210, 40, 123);
 }

 .album-song-button span {
     line-height: 28px;
 }
```

We have some objectives to fulfill at this point of the application.
1. When we click on a song, the song number should change to a pause button.
2. When the mouse leaves the table row of the currently playing song, the pause button should remain.
3. When we switch songs, the previously playing song's table cell should revert the content back to the song number.
4. When we hover over each of the songs that aren't playing, the play button should appear. But, we don't want to show the play button when we hover over the playing song.

1. We need a function that will traverse up the DOM until a parent with the specified class is found.

```
var findParentByClassName = function(element, targetClass) {
  if (element) {
      var currentParent = element.parentElement;
      while (currentParent.className !== targetClass && currentParent.className !== null) {
          currentParent = currentParent.parentElement;
      }
      return currentParent;
  }
};
```
This allows us to write a larger function that will always return a song item. getSongItem() should take an element and use a switch statement that returns the element with the .song-item-number class.

```
var getSongItem = function(element) {
   switch (element.className) {
       case 'album-song-button':
       case 'ion-play':
       case 'ion-pause':
           return findParentByClassName(element, 'song-item-number');
       case 'album-view-song-item':
           return element.querySelector('.song-item-number');
       case 'song-item-title':
       case 'song-item-duration':
           return findParentByClassName(element, 'album-view-song-item').querySelector('.song-item-number');
       case 'song-item-number':
           return element;
       default:
           return;
   }
};
```

We want to store the template for the pause button.
```
var pauseButtonTemplate = '<a class="album-song-button"><span class="ion-pause"></span></a>';
```

Now we create the function that will fulfill "when we click on a song, the song number should change to a pause button".

We create a clickHandler() that will take in a target element
```
var clickHandler = function(targetElement) {
    var songItem = getSongItem(targetElement);
    console.log(songItem);
    if (currentlyPlayingSong === null) {
        songItem.innerHTML = pauseButtonTemplate;
        currentlyPlayingSong = songItem.getAttribute('data-song-number');
    } else if (currentlyPlayingSong === songItem.getAttribute('data-song-number')) {
        songItem.innerHTML = playButtonTemplate;
        currentlyPlayingSong = null;
    } else if (currentlyPlayingSong !== songItem.getAttribute('data-song-number')) {
        var currentlyPlayingSongElement = document.querySelector('[data-song-number="' + currentlyPlayingSong + '"]');
        currentlyPlayingSongElement.innerHTML = currentlyPlayingSongElement.getAttribute('data-song-number');
        songItem.innerHTML = pauseButtonTemplate;
        currentlyPlayingSong = songItem.getAttribute('data-song-number');
    }

};
```

At this point, the click behavior should work; except when the mouse leaves the table cell, the pause button should disappear.

```
var songItem = getSongItem(event.target);
if (songItem.getAttribute('data-song-number') !== currentlyPlayingSong) {
    songItem.innerHTML = playButtonTemplate;
}
```

The code above ensures that the when the mouse leaves the current song, the pause button will remain.

We want to update the code in the mouseover event with a conditional statement that changes the innerHTML of the table cell when the element does not belong to the currently playing song.

```
songRows[i].addEventListener('mouseleave', function(event) {
    var songItem = getSongItem(event.target);
    var songItemNumber = songItem.getAttribute('data-song-number');
    if (songItemNumber !== currentlyPlayingSong) {
        songItem.innerHTML = songItemNumber;
    }
});
songRows[i].addEventListener('click', function(event) {
    clickHandler(event.target);
});
}
```

We're finally ready to create our music player.
Our music player will have three sections: main controls, currently playing, and volume.

```
<section class="player-bar">
   <div class="container">
       <div class="control-group main-controls">
         <a class="previous">
                <span class="ion-skip-backward"></span>
         </a>
         <a class="play-pause">
                <span class="ion-play"></span>
         </a>
         <a class="next">
                <span class="ion-skip-forward"></span>
         </a>
       </div>
       <div class="control-group currently-playing">
           <h2 class="song-name">My dumb song</h2>
           <div class="seek-control">
                <div class="seek-bar">
                    <div class="fill"></div>
                    <div class="thumb"></div>
                </div>
                <div class="current-time">2:30</div>
                <div class="total-time">4:45</div>
            </div>
           <h2 class="artist-song-mobile">My dumb song - Fallout Boy</h2>
           <h3 class="artist-name">Fallout Boy</h3>
       </div>
       <div class="control-group volume">
         <span class="ion-volume-high icon"></span>
           <div class="seek-bar">
               <div class="fill"></div>
               <div class="thumb"></div>
           </div>
       </div>
   </div>
</section>
```
We also add media queries to make our player bar responsive.

```
@media (max-width: 640px) {
     .player-bar {
         padding: 1rem;
         background-color: rgba(0,0,0,0.6);
     }
...
```

Up to this point of our project, we have been using vanilla JavaScript. We can utilize a helper library, JQuery, to do all that we've done so far. It simplifies the development process.

We've refactored our collection and album views and the changes can be view here:
https://github.com/yjhong1004/bloc-jams/commit/31c21bb0f791901986ca4e503c2cf7360917c518

As we continue to refactor our code, we notice that our code is becoming concise and clean. We further clean our code by removing deprecated code, like the findParentByClassName() and getSongItem().

The code can be view here:
https://github.com/yjhong1004/bloc-jams/commit/6f57786a558a5887d54394a9d09fbd597942a6ba

After the refactoring process, we want to continue to develop our application. This time, using JQuery.


We want to use JQuery to implement complex behavior, like moving between songs.
We want to track our current song and album to match the currently playing song's object with its corresponding index in the songs array.
Then, we call the next and previous functions, which would increment or decrement the index of the current song.

We utilize the Buzz library, which allows us to include sounds using the HTML5 audio tag.
We need to consider three states of music: stopped, playing, and paused.
We are able to prevent multiple songs from playing concurrently, to play songs when skipping, and set song volume.

We want to write code so that we can adjust the sound of music. We want to see the song progress and volume changes.
Our song progress is shown via our seek bar. Our seekbar thumb (where the user clicks) involves three new events. 












## Results

Bacon ipsum dolor amet filet mignon meatball spare ribs fatback bacon shankle. Kielbasa andouille fatback salami, boudin bresaola pig alcatra turkey spare ribs jerky. Corned beef bresaola leberkas salami alcatra beef landjaeger venison shank bacon meatloaf beef ribs picanha. Leberkas sausage brisket porchetta shankle prosciutto chicken picanha kielbasa pig kevin t-bone turducken filet mignon jowl.

> Bacon ipsum dolor amet filet mignon meatball spare ribs fatback bacon shankle. Kielbasa andouille fatback salami, boudin bresaola pig alcatra turkey spare ribs jerky. Corned beef bresaola leberkas salami alcatra beef landjaeger venison shank bacon meatloaf beef ribs picanha. Leberkas sausage brisket porchetta shankle prosciutto chicken picanha kielbasa pig kevin t-bone turducken filet mignon jowl.

Bacon ipsum dolor amet filet mignon meatball spare ribs fatback bacon shankle. Kielbasa andouille fatback salami, boudin bresaola pig alcatra turkey spare ribs jerky. Corned beef bresaola leberkas salami alcatra beef landjaeger venison shank bacon meatloaf beef ribs picanha. Leberkas sausage brisket porchetta shankle prosciutto chicken picanha kielbasa pig kevin t-bone turducken filet mignon jowl.

## Conclusion

Bacon ipsum dolor amet filet mignon meatball spare ribs fatback bacon shankle. Kielbasa andouille fatback salami, boudin bresaola pig alcatra turkey spare ribs jerky. Corned beef bresaola leberkas salami alcatra beef landjaeger venison shank bacon meatloaf beef ribs picanha. Leberkas sausage brisket porchetta shankle prosciutto chicken picanha kielbasa pig kevin t-bone turducken filet mignon jowl.
