---
layout: post
title:      "More on React and Redux: Moron, React, and Redux"
date:       2020-08-15 15:22:22 +0000
permalink:  more_on_react_and_redux_moron_react_and_redux
---


Being that this is my *last blog post ever* I thought I'd use the opportunity to walk through the section I had the most trouble learning. *See title, come back when you're ready*

For whatever reason, I didn't wrap my head around React or Redux until I was in my final project. So now, just to prove to myself that I understand it, I'm going to walk through how both of them work together in my **incredibly funny, thought-provoking blog**. Starting, of course, with React. 

*This is gonna be a long one, folks. I'm literally just doing this for my own benefit -- no one should read this! I'm not a trustworthy source of information, nor am I a trustworthy source of entertainment. Those are the two reasons to read long internet posts, so go ahead and change the channel, friend. We're in Self-Indulgence Mode here.*

Alright, now that I'm alone, let's discuss the React I learned here and also touch on the React I learned while desperately flipping through documentation a week-and-a-half ago. Spoiler Alert: They're a little different, but not really. 

The React I learned was fairly discrete. Not dark-alley-mysterious-package film-noir **discreet**, just regular ole *discrete*. Everything is packaged up in containers and components. You're one or you're the other, really. I guess both versions are kind of discrete in this way, but the New Way (TM) just seems a little more...relaxed? I guess?

So, Containers. What makes a component a container? Great question. The short answer seems to be: Containers mess with State. What's State you ask? Lucky for us, it mimics concept pretty well. Concept referring to when people say neat little nothing phrases like "I'm in a New York **state** of mind", or "my dog is in a trance **state**." 

With either of the fantastic examples above, one thing is certain. Billy Joel was not *always* in a New York state of mind! That would be **nutso**. He'd never get anything done if that was the case. And my dog is certainly not always in a trance state, floating above the island in the kitchen! He's only like that because he *wants attention right this minute*. But I'm blogging, bud, so keep on trancing for all I care. I'm getting to the nitty gritty.

So that's what state refers to. A temporary, changeable thing. In a React program, it can be as simple as this:

    The component has a state that contains one property: name.
		
		Upon loading, the name property is an empty string.
		
		The user can update the name to "Jefar, mysterious snake man and creepy-uncle type from Aladdin" by typing those words into an input in the component.
		
		The state is now "Jefar, mysterious snake man and creepy-uncle type from Aladdin"
		
		We have succeeded, finally, in changing that component's local state.
		
Hold the phone -- local state? Am I foreshadowing a non-locally sourced, big pharma, non-organic state that will appear at some point later in our adventure? Stay tuned to hear a definite yes!

Yes, we've done it. We've talked about state, and it's fine I guess. But why do containers have access to state while other components have to get by on nothing at all?

**Well, other components get something even cooler than state, buddy.**

It's actually not cooler at all. It's called Props, which is short for properties. We had to give it a nickname to give us a false sense of familiarity with it. So lets dig into what props are!

Props are assigned to components at birth. Or rather, at render. You see, we have to will these bad boys into existence, and unlike us they're born with a purpose! To do something with these Props! Here's the workflow, simplified as much as I can:

    We got a container, which as we know, has access to a state.
		
		The container renders another component, which is not a container, and passes in the state as *props*
		
		That component takes the props, which it has no power to change, and does something with it -- let's face it, usually it just displays it or something. 
		
		The user smiles a knowing smile, comfortable with what has just transpired.
		
Pretty simple right? And I know that you're freaking out because you've been suppressing an enormous question that'll tear the whole framework apart: "What if I change the state? The props will be outdated, and our user's once-knowing smile will be transfigured to a contorted, unhappy frown!"

You **simpleton**. React would never do that to us, we've been through too much together. The container re-renders every time state is updated, thus re-rendering all of the components that it brought into life as well. 

*Problem solved before it even became a problem, dummy*. 

*Maybe next time do your own research before reading a random person's blog about a topic you have an undetermined amount of knowledge about.*

That's the absolute bare-bones concept of React. There are of course more technical aspects, but if I had to explain it while day-drinking with the ghost of a civil war veteran, that's how I'd explain it. Don't worry, the ghost will drive. 

*Don't ask his opinion on anything.*

So Nathan, if we've got this "perfect framework" that has "no problems" and can "be explained to a spectral anomoly from a darker historical context," what do we need Redux for? Isn't it just there to **make us hate ourselves**? Should we even use something that was only made for pain?

Well, the answer may surprise you.

We shouldn't use Redux! Unless we need it. Which we might. It depends on you, really.

Redux is a great tool for larger, or more complicated, applications. It breaks the conventional wisdom of "don't put all your eggs in one basket" and presents "why do I have a basket that I'm not allowed to put my eggs in? I only bought one basket, and that was its purpose. I don't have to listen to you Edgar, you're from a different time and you keep making me cold when you float through me." 

If you followed that insanely long and unrewarding joke, congratulations! Your reward is me talking more about Redux.

So, you remember when I expertly foreshadowed a somewhat larger, non-local state. Redux helps us make that Cthulu-esque, twelve-story, gargantuan state. It also gives us some tools that allow *any component* to access it. Which is neat. You can essentially just pull that state in anywhere in your app as you decide whether or not a component needs to be a container or merely presentational. 

*So what, is it like, really easy to use? That way you don't get depressed and throw your project away just to have a chance at joy in this life?*

It's not...super easy...

I mean, look -- there's some more conceptual things we have to get out of the way. We'll start with the elements of Redux.

Redux manages state via Actions and Reducers. Actions are things that say stuff like 'ADD_THING' or 'DELETE_THING', 'UPDATE_THING' or even 'LOAD_THINGS'. Reducers listen to those actions yell commands and modify the global state according to what was yelled. If that doesn't help you yet, stick around for some maybe less helpful stuff.

So, let's take an example action. 'ADD_THING' can refer to any 'thing' you can reference in an app. Say we have a bunch of things, and these things have 'attributes' and an 'id'. So, the app lets you, the user, make a thing. You can give the thing an attribute, and save it by clicking a button. 

The component you're in right now has a local state with a property called 'attribute' which you just set to something cool, like "Smokin'". We've got a Smokin' Thing now, so we need to tell the state. How do we dispatch this information??

**The foreshadowing.**

**It's palpable.**

The dispatch method, provided by Redux, is the answer. In that same old nothing component, we have a powerful tool sent from our container method (manually, through props), which it received from being connected to the global state. The dispatch method receives one parameter: an action. The action receives one parameter: a thing. It could be anything, not just our example Smokin' Thing. It depends on what you're up to. In our case, it receives a Smokin' Thing. 

*I regret this example's name, as Smokin' Thing sends more chills up my spine than the civil war ghost bit I keep selling.*

So that looks like this:

> handleSubmit = event => {
> 	 this.props.addThing(this.state)
> }

The handleSubmit thing is just a good way to write functions in React, don't worry too much about that if you're unfamiliar. The important part is that you see that monstrosity between the brackets. Where the hell is dispatch? I said we'd use it and we didn't, what the hell?

Well, I said we'd inherit it from our Container, and we did. That method #addThing isn't just the action by the time it's here, it's shorthand for dispatch(addThing()). In our container, we set it up via a method called #mapDispatchToProps, which, well, maps dispatch to props. The bottom of our container looks like this:

>const mapDispatchToProps = dispatch => ({
>  addThing: thing => dispatch(addThing(thing))
>})

>export default connect(null, mapDispatchToProps)(Container);

So what's happening in mapDispatchToProps is exactly what I just described. We're taking the dispatch method granted to us by redux, passing in the action we define somewhere else, and setting up the param to be a Thing of our own creation. All in the form of a javascript object, the key of which is named addThing. The last line is how we connect to our global state -- the connect method is provided by the react-redux library for such a purpose. 

We then pass this new addThing and all of its inner workings as a prop to our simple component (from our not-simple container) for easy use when we need it. But what exactly happens when we call it upon submission of our Smokin' Thing?

Our reducer processes it, of course. But before we get there, let's discuss exactly what our action looks like.

>export const addThing = thing => {
>  return {type: 'ADD_THING', thing}
>}

That's nothing, right? Just a function that returns an object. What's even happening there?

*Well, this is the fulcrum of the whole operation, moron. Way to insult the fulcrum.*

The action, as you can see, takes one parameter in and returns a JS Object in return. It helps us process the Smokin' Thing (from our non-container component) and tags a type on next to it. What's the type do? Don't worry, we're getting there.

Back to the Reducer!

Think of the reducer as a big If Statement -- because that's what it is. It's more common to use Switch/Case/Default though, because these can get ugly. So, what's it look like? Well, in our example, something like....

```
const thingReducer = ( state = { things: [ ] }, action ) => {
  switch(action.type) {
    case ('ADD_THING'):
		  const newThing = action.thing
		  return {
			  ...state,
				things: [...state.things, newThing]
		default:
		  return state
		}
  }
}
```

There's a lot going on there, but I'll break it down as best I can. So we have a function that accepts two things: a state that has a default of { things: [ ] }, and an action with no default. The #dispatch method provides the action to this reducer when you call it. So when we call this.props.addThing(thing), dispatch is plugging in the action {type: 'ADD_THING} and providing our thing in the hash with it. The state, if there is one, is provided without our input. 

So we're in the thingReducer (regrets) and the only thing our switch statement is concerned with is our action type, which lucky for us, is 'ADD_THING.' Once we're in our proper case, a constant called newThing is created, to which we assign Smokin' Thing. Then, using the power of dots, we copy our state (we don't directly modify the state ever, we only return copies which we've modified). Notice that it's not a perfect copy, though. We've stuck our newThing in our things list, which we're now returning!

This return value is our new state! Tada! Simple, right? No? I know.

It's complicated, and difficult to wrap your head around initially. But you can break it down to dispatching an action to the reducer, which...probably doesn't help. But it's a cycle at least. When you want to change global state, it should be difficult -- it's a very deliberate thing to alter. Consequences are high. It's essentially a localized database you're messing with! But should you decide to, just remember the broad theory:

You have to call #dispatch on an action. The action carries the new information to the reducer. Then, the reducer interprets the action's type ('ADD_THING', etc.) and uses the information provided to alter a copy of the state, which will be returned as the new, updated state. 

That's it! We sure blogged the hell out of that stuff, and here we are on the other side (ghost joke count: a billion). 

If you've read this far, I'm...terribly sorry for your loss. You'll never get that time back, and that's 100% on you. Thanks for reading!

