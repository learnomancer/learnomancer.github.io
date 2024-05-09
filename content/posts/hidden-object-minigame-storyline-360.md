---
title: 'Create a Hidden Object Mini Game in Storyline 360 with Just One Javascript Trigger'
date: 2024-03-25
draft: false
---

In this video tutorial, we'll explore how to click on objects in Articulate Storyline 360 and register those clicks using mouse click event listeners in Javascript. We're going to click on multiple objects affect their properties, all by using only one trigger - the execute Javascript trigger.

To exemplify this, I made a hidden objects mini game. In it, you have to click on each of the objects scattered throughout the slide. Once clicked, the object will move and then disappear. And the name of the object will be crossed off a list. This is really amazing if you want to implement gamification into your projects.

This is something I've been looking forward to do for a long time, and I'm so glad I got it to work! Enjoy!

## Here's the video
{{< youtube zKcNObzkRFs >}}

## Code used

```js {linenos=true}
var shuttle = document.querySelector("[data-acc-text='shuttle']");
var satellite = document.querySelector("[data-acc-text='satellite']");
var lander = document.querySelector("[data-acc-text='lander']");
var telescope = document.querySelector("[data-acc-text='telescope']");

var shuttleText = document.querySelector("[data-acc-text='shuttleText']");
var satelliteText = document.querySelector("[data-acc-text='satelliteText']");
var landerText = document.querySelector("[data-acc-text='landerText']");
var telescopeText = document.querySelector("[data-acc-text='telescopeText']");

let timeline = gsap.timeline();

function addAnimation_MoveAndDisappear(target, targetText){
    timeline.to(target, {y:"-=100", duration:0.5, ease:"power1.out"});
    timeline.set(target, {opacity:0});
    timeline.set(targetText, {opacity:0})
}



shuttle.addEventListener('click', () => {
    addAnimation_MoveAndDisappear(shuttle, shuttleText);
    timeline.play();
});

satellite.addEventListener('click', () => {
    addAnimation_MoveAndDisappear(satellite, satelliteText);
    timeline.play();
});

lander.addEventListener('click', () => {
    addAnimation_MoveAndDisappear(lander, landerText);
    timeline.play();
});

telescope.addEventListener('click', () => {
    addAnimation_MoveAndDisappear(telescope, telescopeText);
    timeline.play();
});

```