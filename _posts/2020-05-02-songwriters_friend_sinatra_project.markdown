---
layout: post
title:      "Songwriter's Friend: Sinatra Project"
date:       2020-05-02 17:58:10 -0400
permalink:  songwriters_friend_sinatra_project
---


So, this was a fun project for me. If Rails makes the processes I did in this easier, I can't wait to learn it. Let's get right into it!

The idea was pretty easy for me. I've been a musician forever, and I love writing songs but I need a place to store them until I can get them recorded. It was just a matter of logistics from there. 

Users would obviously have many songs, and songs would belong to a user. I thought about having a many to many relationship, where co-writers could belong to the song if they were users too, but that quickly overcomplicated otherwise simple things (e.g., who has editing/deleting rights to the song? when a user deletes their profile, do they still show up as a co-author, just as a string rather than a link?). It wasn't worth it to me for something I'm not sure would be a super desirable function. But, I did decide to let Users write in any co-authors they wanted to mention as a simple string, for their own purposes. 

Songs had, along with co-authors, quite a few attributes. A creation date, tempo, time-signature, key, title, and lyrics. Not bad. I did realize though that not all people that wrote songs really knew what some of these things were. So, the title is the only requirement for a song. I also decided to include some dropdown menus for these less-musically-literate users to potentially use. 

I had the most fun designing the song's new view and the edit view. They're nearly identical, except the edit page loads the existing song information into the inputs and dropdowns for the user to see before they change things. This, I thought, was pretty elegant - and it's a feature that I could see being in real applications. So that was exciting, even if the coding was a bit tedious at first. 

I googled a lot of stuff during this project, mostly html related. For instance, I had no idea how to make a dropdown selector. I'd learned it previously, but I wayyy forgot it. I also needed a refresher on textareas, and filling in information on dropdowns/textareas. It was frustrating, but rewarding. 

I really liked putting the app together. I liked playing around in shotgun, creating songs and seeing what looked weird and off, trying to break my app into letting me edit other user's songs, and even making small features, like allowing the user to login with either their email or their username in the same textbox. I thought that was really cool, and my wife really didn't get that feeling at all - probably because I hyped it up too much. It's fine though. I know it's cool. 

Anyway, putting Songwriter's Friend together was fun. So much so that I wanted to dress it up with more features, and add colors/formatting and try to make it more "real." But, I didn't want to make it more difficult to assess, and I really need to move past the project and on to the rest of the curriculum. It was very much worth doing though.
