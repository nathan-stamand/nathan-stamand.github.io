---
layout: post
title:      "Portfolio Project 4: RipChorder, a Song Constructor"
date:       2020-07-15 05:42:50 +0000
permalink:  portfolio_project_4_ripchorder_a_song_constructor
---

I got the idea for this project from an app that I used to have before I switched my phone to an Android - I haven't found an equivalent one yet so I decided to start making a replacement. The app acts as an encyclopedia of chords you can add to feeds so you can play through them and make judgment on how they work together. I used to use it when I was away from my piano or guitar but wanted to write songs.

I knew I couldn't make the ideal version of the app yet, because it was extremely 'smart' - it allowed you to customize chords in various ways, it provided not only the basic triads (3-note chords) of the key, but also a myriad of more complex chords (all in key) and some commonly used chords with accidentals (any note out of key). You could also transpose the song after it was written (or during). And as an added feature, it showed every note in the chord with accidentals highlighted. It was phenomenal, and I miss it dearly.

My application's much simpler, for the time being at least. Currently, the features are that the key's triads are provided as buttons that play the chord and add it to the feed, users can create custom chords from three selectors, users can play/pause/stop songs they write, save the songs for access later (their custom chords are also saved), and delete songs they don't want. Already a much simpler app, but still turned out to be very difficult to create. As usual, I learned a lot.

The first issue was getting sound at all. I wasted hours trying to find the libraries I needed to get 1.) the ability to play sound based off of a chords info (notes, pitch), and 2.) information about a substantial amount of scales, chords, etc. I finally settled on Tone.js and Scribbletunes, which solved each problem respectively. There was a big learning curve, but I eventually figured out how to play notes, and then built a framework for constructing chords via iteration over a list of notes. 

I also struggled with the structure of the application's frontend and backend. I tried a few configurations, and even tried to make a user class complete with signins and authentication, but realized I couldn't reasonably make it work right now. It added too much complexity and a rails backend doesn't seem designed for it. 

I finally settled on this structure for the backend: Songs have many ChordFeeds.

Songs have one title, key, mode (major or minor), and tempo.

ChordFeeds have a position (1 - 4) and a chord_array (max 8 chords).

The frontend has much more going on, and I may still need to refactor and add more classes to clean everything up, but the basic layout is as follows: an App is created, which in turn creates a Songs and ControlPanel. Everything else stems from these two things. Songs pulls the database's songs (with help from its adapter) and renders them into a hidden list (click to unhide) on the page along with Delete and Show buttons for each. As it renders the songs, it creates individual Songs with their json data. Each song in turn creates a ChordFeeds and a ChordContainer with functions of their own.

As I said, it certainly gets more complex on the frontend. I won't get into the methods I made for these classes, but there are quite a few in the ControlPanel (as the name of the class implies, a lot of logic is built in here as it contains the play/pause/stop buttons as well as save, clear, and new). 

A common mistake I made going through the app at first was trying to modify the DOM and the frontend class objects at the same time. I later discovered the cleaner method of manipulating the DOM, saving to the database, and then re-rendering the songs/chord_feeds based off of the database. I made a lot of use of jquery about halfway through working, which I was a little slow to re-learn (we only cover so much in the curriculum) but in the end became pretty comfortable with.

I also learned a lot about asynchronous functions, and not only in the context of fetch statements. I also created #sleep and use it in a few of my classes, primarily to rest between iterating over chord feeds' chords. Based on the tempo (which are measured in beats per minute, or bpm) I would set the sleep timer to 60,000 milliseconds divided by the tempo between playing chords, which required the use of the await in a few methods. I also use await/async methods when iterating and saving chord feeds (they locked up the database unless I waited 50 or so milliseconds between iterating fetches). It was incredibly frustrating but ultimately rewarding when it started working.

In the end I have an app that does what I wanted on some level, though I wouldn't consider it complete until I have more of the functions I wanted originally. I'm very happy with the project overall, even though it's in dire need of refactoring I'm sure. It has restrictions (for ease of completing the project - I'd like to add features that eliminate the limitations) like limiting the amount of chord feeds a song has to 4 and limiting the chords per feed to 8. Hopefully, I can revisit this project and bulk it up to have the functions I've mentioned earlier - I'd really like to use this in the future!
