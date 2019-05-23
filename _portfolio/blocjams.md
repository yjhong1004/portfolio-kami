---
layout: post
title: BlocJams
thumbnail-path: "img/blocitoff.png"
short-description: Build a digital music player, similar to Spotify.

---

{:.center}
![]({{ site.baseurl }}/img/blocitoff.png)


## Summary

BlocJams is a Javascript web application that streams music.

## Explanation


We utilized front end technologies to develop a music player, similar to Spotify. We'll start by creating a skeleton structure of the app, using HTML. We'll add styling and responsiveness using CSS. Lastly, we'll increase interactivity with Javascript.

## Problem

Our users need to access a landing page, designed with our theme in mind. Since this is a front end project, we want to not only keep functionality in mind, but also design.

## Solution

In order to accomplish our goal of creating a music player application, we coded our skeleton HTML structures for each page: landing, collection view, and album view.

Landing page:

We split the landing page into different sections to organize our code properly. We have our navigation bar at the top of the page. We also have our "hero" container, which will be in the middle of our page. This is intentional as we want this section to be shown in greater detail. Lastly, we have our selling points section, which holds different icons. The selling points section is also split into three event sections, each representing different information about our application.

Since our landing page is the first page that our users will access, the focus is really on design. We utilized a combination of CSS and Javascript to dynamically display our landing page features.

Javascript functions will activate the CSS transitions and update the styles from what we've placed in the CSS file to the new styles in the script.
Our application should know when to trigger the animations.

In addition to design, we want our application to be responsive.

What is responsive design?

Since each browser renders certain styles differently, we utilized normalize.css, to make browsers render all elements in line with modern standards. We wanted to make sure that our website is accessible on all devices and shown properly on all screen sizes. We set the viewport meta tag in our <head> tag, which indicates how the browser should render the content in the device's window.

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```
We also added media queries, which helped to apply styles conditionally and by utilizing parameters.

Collection page:

The collection view is to display a user's album collection. We first start off by creating a skeleton HTML structure, add styling using CSS, and display placeholder album data, which will eventually be dynamically generated using Javascript.

Album page:

The album view displays an album's title, artist, record label, and song list. Like the pages that came before it, we implement its structure using HTML, add styling using CSS, and integrate dynamics using Javascript. The album page is where we created the music player using the Javascript Buzz Library. We are able to play/pause, play next or previous songs, toggle the song position, and adjust the volume.

With our music player, we have have some objectives to fulfill:
1. When we click on a song, the song number should change to a pause button.
2. When the mouse leaves the table row of the currently playing song, the pause button should remain.
3. When we switch songs, the previously playing song's table cell should revert the content back to the song number.
4. When we hover over each of the songs that aren't playing, the play button should appear. But, we don't want to show the play button when we hover over the playing song.


Up to this point of our project, we have been using vanilla JavaScript. We can utilize a helper library, JQuery, to do all that we've done so far. It simplifies the development process.

We've refactored our collection and album views and the changes can be view here:
https://github.com/yjhong1004/bloc-jams/commit/31c21bb0f791901986ca4e503c2cf7360917c518

As we continue to refactor our code, we notice that our code is becoming concise and clean. We further clean our code by removing deprecated code, like the findParentByClassName() and getSongItem().

The code can be view here:
https://github.com/yjhong1004/bloc-jams/commit/6f57786a558a5887d54394a9d09fbd597942a6ba


## Results

Heroku link

## Conclusion

Through this project, I've learned how to build a fully functional music player, similar to applications like Spotify. We utilized front end tools like HTML, CSS, Javascript to build our app. We also used a library, JQuery, to refactor our code, so that it is concise and clean.
