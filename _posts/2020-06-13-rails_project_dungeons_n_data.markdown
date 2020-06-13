---
layout: post
title:      "Rails Project: Dungeons 'n' Data"
date:       2020-06-13 19:48:38 +0000
permalink:  rails_project_dungeons_n_data
---

I got the idea for this project from listening to one of my favorite podcasts ("The Adventure Zone" by the McElroy Brothers); it's a show about three adult brothers and their father playing a game of Dungeons 'n' Dragons. It's been a while since I've played D'n'D, but it made me think of game management. I didn't like having to use pencil and paper to write, rewrite, erase, etc. all of the stats and notes from the game. I'm a much faster typer, and it would be nice if there were a <em>database</em> keeping track of the characters and games for me. So, I got started on the logistics of what models I needed.

I ended up needing a model for Campaign, Character, Dnd_Session, Player_Campaign (join table I added later), and finally, User. Because Users could be 'Dungeon Masters' (the players who create and run the story of the campaign) or regular players of the game, I had to create a few aliases to accomodate the relationships. The same User could have many created_campaigns and many play_campaigns, every Campaign has one dungeon_master and can have many players and Characters. The aliasing took a while to perfect, but it was necessary and made the relationships replicate real life. I had to do an embarrassing and excessive amount of console testing to be sure it worked.

My first real obstacle was setting up third party login with OAuth, though. I had a basic signup/login set up already, but once I got to OAuth for Google I had to reach out to my fellow students because I don't have a Facebook so I couldn't follow along properly for the lesson in the Rails section. It turns out I was pretty close, which was exciting in retrospect, but incredibly frustrating at the time. But the video I was recommended helped tremendously.

Afterwards it was smooth sailing for a time as I was just filling in basic controller functions - broad strokes at first, so it was great. Then, as it got more fine-tuned, it became tedious again. I was coding everything into the views and the controller trying to just get the functions and conditionals to work correctly, so once I did that, I had the fun task of outsourcing logic to helpers and models by the droves, and then reworking those methods into smaller, more concise methods. That, I enjoyed. It's nice seeing code cleaned up. 

I won't go into detail with handling everything required for this project;  suffice it to say that I got incredibly familiar with the rails documentation. I needed to do it though, because this really tested my memory of creating scopes, validations, relationships, layouts, and so many more "small things" I didn't think were a big deal. I can now honestly say I've gained an appreciation for Rails that I couldn't have predicted. It's a great system for making these types of websites. 

As of yet I haven't added CSS to the project at all. I wanted to, but I've already spent so much time on this because, well, I tossed my initial project halfway through it. It was a Book Club app, and it was garbage. I didn't think it had enough of my own character in it. I wasn't passionate about it, so I finally scrapped it because I wanted the project to be something I'd enjoy making and hopefully using at some point. I'm happy with my final decision, but it cost me a lot of time that I wish would have been spent moving on in the curriculum. Oh well, c'est la vie. I'm happy with the functionality I was able to implement. It also motivated me to read the style guides for Rails and Ruby, which I didn't know existed but were tremendously helpful in cleaning everything up. I even learned some cool technical stuff from it. 

In conclusion, this was hard. And great. I feel great now at the end of it, but it was difficult and time-consuming because I didn't know Rails like I thought I did.


