---
layout: post
title:      "Final Project: DIY With Me"
date:       2020-08-14 20:09:44 +0000
permalink:  final_project_diy_with_me
---


I'd like to just start out by saying one thing: React and Redux is hard in the weirdest way. 

I really hit my stride in the pure Javascript with Rails backend project - it was straightforward enough, you could force things to work with enough effort. There were no routes, containers, components, etc. It was just churning out script. I could put in the time and know I'd get there well enough.

With React/Redux, it was a struggle from the beginning. I struggled to learn every single aspect of this framework. 

First, I struggled with Routing.

I read everything I could related to react-router-dom. 

One of the main issues I had was that some routes weren't redirecting or loading their components. Turns out that you only need one set of BrowserRouter tags in your app, and adding more leads to complications. It didn't say that explicitly anywhere, I just finally realized it. 

It's hard to visualize things when they were compartmentalized in different components -- at least for me. 

I really should have wire-framed the application out, honestly. Drawing the pages would have probably helped me, because like I said, the visualizing aspect seems like the key to using React. 

Another issue I had was with the Redirect element. Here's how I wanted it to work:

    Click a button (something like Create Project)

    Button calls method named redirectCreateProject

    There's a <Redirect to={'/new'} /> returned in that method

    The user is happy and redirected properly
		
That's...not how it works. Because buttons can't pull an element into themselves. 

So I wasted a fair bit of time on that before finding withRouter, which is a super helpful method from react-router-dom. It basically grants those ever-helpful methods that have to do with the address bar (history, match, location, etc.) to whatever component you're in. So the way I handled redirecting with buttons/methods changed. It now became this:

    Click a button
		
		Button calls method
		
		Method calls this.props.history.push(`${this.match.url}/{insert modifier here}`)
		
		The user is happy and redirected properly
		
So that was a bit of a breakthrough. I'm not a fan of links in applications, if you couldn't tell. I use them pretty rarely -- buttons always look cleaner to me for stuff like this. 

Anyway, onto the details of how I made DIY With Me.

I started with the terminal command for setting up a react application, and installed some support like react-router-dom and cuid (for making unique keys). My idea was basically to make a formatted DIY blog for personal use. My wife actually gave me the idea, because she's started about a million 'Pandemic Projects' since she doesn't work in the summer. 

So, in an abstract sense, I knew I needed mainly two levels of information: a Project Level, and a Step Level. A project has many steps, so that's how I went about starting. 

I set up my API in rails to have basic details that I'd refine later. I knew, for instance, that a project has materials, a description of some sort (I settled on 'blog'), and a name -- a step would have only a description and a time, really. I added header though, for additional clarity. Initially I had materials for each step as well, but decided against it.

I went through a lot of processes in figuring out how to build this app, so I'll spare you the mistakes and tear-jerking debugging stories. In its current form, it's got two containers (three if you count the App.js file) -- ProjectContainer and StepContainer. Due to the nature of the relationship, the StepContainer contains a single prop from ProjectContainer, the project being displayed. Otherwise, they rely on the shared state provided by Redux. 

These containers pull actions from the two files in my actions folder for various purposes. I kept it pretty clean, honestly. StepContainer only pulls step actions, ProjectContainer pulls project actions. App pulls from both for its initial loading from the database. It's a sweet little operation. 

I don't bother with purely functional components (although I wanted to from the beginning) because every time I wanted to make a pure functional component I'd end up wanting some aspect of a class component later. So I gave up on that clean look for convenience more than anything, though if I decide to work more on this project (when I don't hate it as much for hurting my ego) I may change my mind. 

So each container feeds into their lower-life-form stateless components. You can add, delete, update, and view Projects as well as Steps, so I won't bore you with details on what implementing that looks like. Suffice it to say, there's pretty much a component for every CRUDdy action. The part I like the most is that I set up the StepContainer to render a projects steps based on the location in the url, so when you click to edit a Step, it changes the url and renders the Step with inputs and textareas filled with its information rather than just paragraph elements. 

Messing with the database using React-Thunk was a process in and of itself. It took many tries and a lot of tweaking to do anything there, it felt like every action was a snowflake in a sense. Sometimes I didn't need to reload the projects/steps from the database, but sometimes I did -- I'm not sure why. I just did what I had to with that. I think I gathered a much more comprehensive idea of The Scary Redux Process (TM) thanks to having to fool around with the Reducer/Actions as much as I did, but it still feels like there's more to learn there, so maybe I'll do a deep dive on that for my last blog. 

Anyway, I ended up with a project that (as far as I can tell) fulfills all of the requirements a final project should -- I'm off to turn it in. Thanks for reading!

