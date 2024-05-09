---
title: 'Morph Transitions in Storyline 360 with Match Cuts'
date: 2024-03-10
draft: false
---

In this video tutorial, I try and replicate a morph effect in Articulate Storyline 360 by using match cuts. This is like using a sleight of hand, performing an illusion where one element seems to change shape and become the other.

When, in fact, all we're doing is cutting in the middle of an animation and inserting another animation in there, and our eye is fooled into thinking that the animation continues seamlessly.

We are first going to fake this morph effect by using motion paths, then we'll move onto the GSAP Javascript library, so we have more control over our animation.

The idea came to my mind after watching a video from MotionXP and Ben Marirott.

Given that morph transitions are something many Storyline users want due to its popularity in Powerpoint, perhaps such an effect will soothe our spirits until Articulate decides to implement it.


Referenced video, by MotionXP :  https://www.youtube.com/watch?v=zikOzJUtWr4

## Here's the video
{{< youtube 9PmlSLMTVwM >}}

## Code used

```js {linenos=true}
var triangle = document.querySelector("[data-acc-text='triangle']");
var square = document.querySelector("[data-acc-text='square']");


var timeline = gsap.timeline({
    repeat:-1,
    yoyo:true,
});

gsap.set(square,{opacity:0});

timeline.fromTo(triangle,{xPercent:0, rotation:"-=20"},{xPercent:"+=150", rotation:0, duration:1, ease:"elastic.in"});
timeline.set(triangle,{opacity:0});

timeline.set(square,{opacity:1, rotation:0});
timeline.fromTo(square,{xPercent:"-=150"},{xPercent:0, rotation:20, duration:1, ease:"elastic.out"});


```

```js {linenos=true}

///---------------------ROTATION----------------

var triangle = document.querySelector("[data-acc-text='triangle']");
var square = document.querySelector("[data-acc-text='square']");


var timeline = gsap.timeline({
    repeat:-1,
    repeatDelay:1,
    yoyo:true,
});

timeline.set(square,{opacity:0});

timeline.to(triangle,{rotation:360, duration:1, ease:"elastic.in"});
timeline.set(triangle,{opacity:0});

timeline.set(square,{opacity:1});
timeline.from(square,{rotation:-360,duration:1, ease:"elastic.out"});


```