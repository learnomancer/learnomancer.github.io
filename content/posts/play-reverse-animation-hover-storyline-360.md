---
title: 'Interactive Storyline 360: Play and Reverse Animations on Hover with Javascript & GSAP'
date: 2024-04-03
draft: false
---

In this video tutorial, we'll experiment with event listeners for mouse hover using an execute Javascript trigger in Articulate Storyline 360. These event listeners will allow us to trigger some animations when the mouse hovers over an object, and when the mouse leaves the bounding box of an object.

We will use these event listeners to play a GSAP animation timeline when we hover the mouse over a png image, then reverse (or rewind) the animation when the mouse no longer hovers on the image.

I think this is a really easy to achieve effect, and the result is so much more responsive than the effect Storyline offers by default. I hope you enjoy this and use it in your projects!

Check out the GSAP documentation featured in this video here:
https://gsap.com/resources/getting-started/control/#control-methods

## Here's the video
{{< youtube bQ8SEf_s-p4 >}}

## Code used

```js {linenos=true}

var drink = document.querySelector("[data-acc-text='drink']");
var leaf = document.querySelector("[data-acc-text='leaf']");

let timeline = gsap.timeline();

function addAnimation_Move(target){
    timeline.to(target, {y:"-=100", duration:0.5, ease:"power1.out"});
}

drink.addEventListener('mouseover', () => {
    addAnimation_Move(leaf);
    // Play the timeline forward
    timeline.play();
});


drink.addEventListener('mouseout', () => {
    addAnimation_Move(leaf);
    // Reverse the timeline
    timeline.reverse();
});

```